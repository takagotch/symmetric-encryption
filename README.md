### symmetric-encryption
---
https://rocketjob.github.io/symmetric-encryption/


```ruby
SymmetricEncryption.encrypt "Sensitive data"
SymmetricEncryption.decrypt "XXXXXXXXXXX"

config_file = Rails.root.join('config', 'redis.yml')
raise "redis config not found. Create a config file at: config/redis.yml" unless conifg_file.file?

cfg = YAML.load(ERB.new(File.new(config_file).read).result)[Rails.env]
raise("Environment #{Rails.env} not defined in redis.yml") unless cfg

SymmetricEncryption::Reader.open('encrypted_file') do |file|
  file.each_line do |line|
    puts line
  end
end

SymmetricEncryption::Writer.open('encrypted_file') do |file|
  file.write "Hello World\n"
  file.write "Keep this secret"
end

SymmetricEncryption::Write.open('encrypted_compressed.zip', compress: true) do |file|
  file.write "Hello World\n"
  file.write "Keep this secret"
end

SymmetricEncryption::Writer.open('encrypted_compressed.zip', compress: true) do |file|
  file.write "Hello World\n"
  file.write "Compress this\n"
  file.write "Keep this safe and secure\n"
end

```

```
production:
  adapter: mysql
  host: db1w
  database: myapp_production
  username: admin
  password: <%= SymmetricEncryption.try_decrypt "XXXXXXXXXXXXX\n"%>
```

```
gem 'symmetric-encryption'
bundle install

```

