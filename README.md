## subdomain 配置与实现（Rails 4.0）

步骤如下：
### 在 config/routes 中添加
```ruby
constraints(subdomain: 'xxx') do 
  get '/' => 'controllerName#actionName'
end 
```
 

### 在lib文档中添加一个 subdomain.rb
```ruby
class Subdomain 
  def self.matches?(request)
    request.subdomain.present? && request.subdomain != "www" 
  end 
end
```
 

### 在 config/application.rb 中添加
```ruby
config.autoload_paths += %w(#(config.root)/lib )
```
 

### subdomain.yourdomain.com
