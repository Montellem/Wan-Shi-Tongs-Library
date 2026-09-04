# Distinct, Union, Intersect and Except

## What is it?

These are set operations: `Distinct` removes duplicate elements, `Union` combines two sequences without duplicates, `Intersect` keeps only elements present in both sequences, and `Except` keeps elements from the first sequence that are not present in the second.

## Example

```csharp
List<string> importedBrands = new List<string> { "Toyota", "BMW", "Toyota", "Ford" };
List<string> allowedBrands = new List<string> { "Toyota", "BMW", "Audi" };

var uniqueBrands = importedBrands.Distinct();                 // Toyota, BMW, Ford
var allBrandsCombined = importedBrands.Union(allowedBrands);  // Toyota, BMW, Ford, Audi
var validBrandsOnly = importedBrands.Intersect(allowedBrands); // Toyota, BMW
var invalidBrands = importedBrands.Except(allowedBrands);     // Ford
```

## How does it work?

All four methods compare elements using the default equality comparer (or a custom `IEqualityComparer<T>` if provided). Internally, LINQ builds a hash set from the relevant sequence(s) to efficiently check membership, so these operations are much faster than manually comparing every element to every other element with nested loops. For custom objects (like `BankAccount` or `Car`), you typically need to override `Equals`/`GetHashCode`, or provide a comparer, for these methods to work as expected.

## When should I use it?

* Cleaning imported data that may contain duplicate rows (`Distinct`)
* Validating imported values against a list of allowed values (`Intersect`, `Except`) — directly relevant to validating `.txt` import files against expected categories
* Combining two data sources into one deduplicated list (`Union`)
* Finding what's missing or invalid by comparing an imported set against a reference set (`Except`)

## Common Mistakes

* Using these methods on custom objects without a proper `Equals`/`GetHashCode` override, causing "duplicates" to not be detected because each object is compared by reference instead of by value
* Forgetting that `Except` is not symmetric: `a.Except(b)` is not the same as `b.Except(a)`
* Assuming `Union` requires the two sequences to have the same length or type structure — it only requires the same element type
* Not realizing these methods do not preserve original ordering after deduplication in all cases

## Practice

**Task:**
Simulate importing a list of product group names as `List<string>` with some duplicates. Use `Distinct` to clean it. Then compare it against a reference `List<string>` of valid product groups using `Except` to find any invalid entries that should be flagged during import.

**Goal:**
Be able to use set operations for data validation and cleaning scenarios like those in the dashboard's import pipeline.
