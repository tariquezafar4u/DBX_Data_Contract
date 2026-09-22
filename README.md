# Data Contract Repository (Learning Project)

This is a **simplified learning version** of a data-contract repository. It holds one
data contract per data product. The DAT-EDIP framework reads these contracts to know:

- where the source data lives (Volume path)
- where the target Raw/Stage tables live
- the column schema and data types
- the primary key
- nullability rules
- basic validation rules
- who owns/develops the product

## Structure

```
contracts/
  customer_orders/
    contract.yaml      <- the actual data contract
schema/
  contract.schema.json <- JSON Schema used to validate contract.yaml shape
```

## Adding a new data product

1. Create a new folder under `contracts/<product_name>/`.
2. Copy `contracts/customer_orders/contract.yaml` as a template.
3. Fill in `product_name`, `owner`, `source`, `target`, `columns`, `primary_key`,
   and `validations`.
4. Commit and deploy this repository first, **before** deploying DAT-EDIP.

## How DAT-EDIP consumes this

The DAT-EDIP framework's `contract_loader.py` reads `contract.yaml` for a given
product name and turns it into a plain Python object used by the Raw Manager and
Stage Manager notebooks. In this learning setup the contract file is simply copied
next to the framework config (or read directly from its Volume/Repo path) — no
network call is required.
