# Search Criteria


## Criteria 

`Filter Group && Filter Group && ...`

## Filter Group

`(Filter || Filter || ...)`

## Example

Return only active pickup locations (`is_active = 1` **AND** `is_pickup = 1`):

```php
/**
* @param bool $isReturnOnlyActive
* @return SearchResultsInterface
*/
public function getPickupLocations(bool $isReturnOnlyActive): SearchResultsInterface
{
    $criteria = $this->searchCriteriaFactory->create();
    $filterGroups = [];

    if ($isReturnOnlyActive) {
        $activeFilter = $this->filterBuilder
            ->setField(CenterInterface::IS_ACTIVE)
            ->setConditionType('eq')
            ->setValue('1')
            ->create();

        $activeFilterGroup = $this->filterGroupFactory->create();
        $activeFilterGroup->setFilters([$activeFilter]);
        $filterGroups[] = $activeFilterGroup;
    }

    $isPickupFilter = $this->filterBuilder
        ->setField(CenterInterface::IS_PICKUP)
        ->setConditionType('eq')
        ->setValue('1')
        ->create();

    $isPickupFilterGroup = $this->filterGroupFactory->create();
    $isPickupFilterGroup->setFilters([$isPickupFilter]);
    $filterGroups[] = $isPickupFilterGroup;

    $criteria->setFilterGroups($filterGroups);

    return $this->getList($criteria);
}
```