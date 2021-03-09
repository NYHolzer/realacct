## 3/8/2021
My goals for today's coding is to get the building index all hooked up and perhaps start on the apartments. 
Along the way, I also hope to answer questions that come up and note them here for future reference.

### Markdown Learnings
[Cheat Sheet for Markdown](https://www.markdownguide.org/cheat-sheet/)

1. How to open preview markdown vscode
`ctrl + k v`

### Ruby on Rails Column Types
2. [Ruby on Rails column types](https://fullstackheroes.com/rails/column-types/)
```
NATIVE_DATABASE_TYPES = {
  primary_key: "bigint auto_increment PRIMARY KEY",
  string:      { name: "varchar", limit: 255 },
  text:        { name: "text" },
  integer:     { name: "int", limit: 4 },
  float:       { name: "float", limit: 24 },
  decimal:     { name: "decimal" },
  datetime:    { name: "datetime" },
  timestamp:   { name: "timestamp" },
  time:        { name: "time" },
  date:        { name: "date" },
  binary:      { name: "blob" },
  blob:        { name: "blob" },
  boolean:     { name: "tinyint", limit: 1 },
  json:        { name: "json" },
}
```
- :primary_key - translates into whatever the primary key datatype your database of choice requires
- :string - use for short strings such as names and emails
- :text - use for long strings, normally captured by textarea
- :integer - it's a whole number, eg. 0,12,12532
- :float - decimal numbers stored with fixed floating point precision
- :decimal - stored precision varies; good for exact math calculations
- :datetime - both date and time
- :timestamp - same as datetime; usually used for created_at/updated_at
- :time - hours, minutes, seconds
- :date - year, month, day
- :binary - store images, videos and other files in their original format in chunks of data called blobs
- :blob - similar to binary, contains the metadata about a file. Blobs are intended to be immutable
- :boolean - self explanatory - true/false
- :json - from Rails 5 onwards, you can natively store JSON values thanks to this Pull Request. A lot of people still use Postgres' jsonb datatype though.

### How to handle images in Ruby on Rails?
Ideally, developers in the past have used [paperclip](https://github.com/thoughtbot/paperclip) to help save the files to cloud servers. However, now Rails actually has its own [Active Storage](https://guides.rubyonrails.org/active_storage_overview.html)

*For when I'm ready to learn: [Hackernoon's Uploading Files Into Ruby On Rails ActiveStorage](https://hackernoon.com/uploading-files-into-ruby-on-rails-activestorage-gv1r3ukr)*

**DECISION: For now, we will just use blob or binary to store images of Buildings as current project will just have a few buildings.**

*// Down the road: Plan to build out a utility for a manager to take pictures at an apartment and upload them to the cloud for future use and take notes. Then the ability to email the photos to owners or relevant parties for things that need to be fixed etc. - At that time we will make use of ActiveStorage* 

> Wait, what's better blob or binary to store images in the database? 
