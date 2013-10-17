# Bootsy Changelog

## master

* Migrated Bootsy to Bootstrap 3.

## 1.2.0

* Merged the [SimpleForm](https://github.com/plataformatec/simple_form) support into master.
  You no longer need to use the [bootsy-simple_form](https://github.com/volmer/bootsy-simple_form)
  gem in your project.

## 1.1.0

* Design and interaction improvements. Bootsy is a lot more 'ajaxy' now, and loads images
  without flashing. This also changed the way deleting an image works. It no longer
  'refreshes the gallery', but instead finds the element to delete, fades it out,
  and removes it (thanks @anthonycollini).
* Fixed the indent and outdent icons as the icons were reversed from what they
  should be (thanks @anthonycollini).
* `z-index` fix to allow the contextual drop-down menus to properly appear over the footer and
  modal if it includes a longer list (thanks @anthonycollini).
* A default message if there are no uploaded images (thanks @anthonycollini).
* Bootsy now uses [Bootstrap File Input](https://github.com/grevory/bootstrap-file-input) with
  auto submission on file input change (thanks @anthonycollini).

## 1.0.0

* Now Bootsy is compatible with Rails `4.0` - *Backwards incompatibility*: Bootsy does not support
  Rails `3.2` anymore. We strongly recomend to move on and upgrade outdated projects to Rails `4.0`.
  If you didn't upgrade your project yet, you can use
  [our branch with *temporary* support for Rails `3.2`](https://github.com/volmer/bootsy/tree/rails-3.2).
* Bootsy now accepts file storage in cloud services like Amazon S3 and others.
  In `config/intializers/bootsy.rb`, just set a new attribute called `storage`
  as :fog. If you do that, please add 'fog' to your Gemfile and create and
  configure your service's credentials in an   initializer file, as described in [Carrierwave's docs](https://github.com/carrierwaveuploader/carrierwave/blob/master/README.md#using-amazon-s3).
* It is possobile now to delete orphan image galleries. Just call `.destroy_orphans` with a time limit:

```ruby
Bootsy::ImageGallery.destroy_orphans(1.day.ago)
```

* Now it's possible to fully clear the editor in the client side, by calling the function `clear()` in your Bootsy area:

```javascript
Bootsy.areas[0].clear();
```