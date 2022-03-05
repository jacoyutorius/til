# カラム削除マイグレーションのかっこいい書き方

`#revert` を使う。

e.g)

```bash
# tree db/migrate/
db/migrate/
├── 20220305125806_create_users.rb
├── 20220305125837_add_address_to_users.rb
└── 20220305125903_remote_address_from_users.rb
```

```ruby
require_relative '20220305125837_add_address_to_users'

class RemoteAddressFromUsers < ActiveRecord::Migration[6.1]
  def change
    revert AddAddressToUsers
  end
end
```