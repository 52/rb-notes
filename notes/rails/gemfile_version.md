## Version trong `Gemfile`
### `>=`
Luôn install version mới nhất (install the lastest version available)
```ruby
gem 'carrierwave', '>= 1.1.2'
```

### `~>`
Install version mới, nhưng chỉ được khác biệt chữ số cuối cùng
Ví dụ:
```ruby
gem 'puma', '~> 3.1.1'
```
Có thể install các version mới hơn như `3.1.2`, `3.1.3`. Nhưng không được update version `3.2.0`, `3.2.1`, `3.3`

### `exact version`
```ruby
gem 'turbolinks', '5.0.1'
```

Install đúng version `5.0.1`