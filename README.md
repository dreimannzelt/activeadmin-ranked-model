# Active Admin Ranked Model

This gem extends ActiveAdmin so that your index page's table rows can be
sortable via a drag-and-drop interface.

It's heavily inspired by [activeadmin-sortable](https://github.com/neo/activeadmin-sortable)

## Prerequisites

This extension assumes that you're using one of the following on any model you want to be sortable.

#### ActiveRecord

[ranked-model](https://github.com/mixonic/ranked-model)

```ruby
class Page < ActiveRecord::Base
  include RankedModel
  ranks :manual_order
end
```

## Usage

### Add it to your Gemfile

```ruby
gem 'activeadmin-ranked-model'
```

### Include the JavaScript in active_admin.js

```javascript
//= require activeadmin-ranked-model
```

### Include the Stylesheet in active_admin.css
```css
//= require activeadmin-ranked-model
```

Place this require line before Active Admin's own import lines.

### Configure your ActiveAdmin Resource

```ruby
ActiveAdmin.register Page do
  config.sort_order = 'manual_order'
  config.paginate   = false # optional; drag-and-drop across pages is not supported

  ranked(:manual_order) # creates the controller action which handles the sorting

  index do
    ranked_handle_column(:manual_order) # inserts a drag handle
    # other columns...
  end
end
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
