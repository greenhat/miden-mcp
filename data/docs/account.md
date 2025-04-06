# Miden Accounts

TBD

## Storage

The account storage in Miden is defined using the `storage` attributes.

For example:

```rust
#[component]
struct MyAccount {
    #[storage(
        slot(0),
        description = "test value",
        type = "auth::rpo_falcon512::pub_key"
    )]
    owner_public_key: Value,

    #[storage(slot(1), description = "test map")]
    asset_qty_map: StorageMap,
}

impl foo::Guest for MyAccount {
    fn set_asset_qty(pub_key: Word, asset: CoreAsset, qty: Felt) {
        let my_account = MyAccount::default();
        let owner_key: Word = my_account.owner_public_key.read();
        if pub_key == owner_key {
            my_account.asset_qty_map.set(asset, qty);
        }
    }

    fn get_asset_qty(asset: CoreAsset) -> Felt {
        let my_account = MyAccount::default();
        my_account.asset_qty_map.get(&asset)
    }
}
```

Both `Value` and `StorageMap` expose only `get` and `set` methods.

