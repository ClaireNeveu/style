ADT fields should be strict in the general case. This usually reduces memory usage without impacting CPU usage. There are exceptions.

The standard indentation level is 4; indentation should always be done with spaces. When the line begins with a separator such as "," or "|", the separator counts as whitespace for the purposes of indentation.

In an ADT definition, the first constructor should always begin on the next line, unless the whole definiton can fit on one line.
```
data Foo 
  = Bar Int Int Int
  | Baz String String String
  | Qux Int String
  deriving (Show)

data Post =
  { headline :: Text
  , title :: Text
  , body :: Text
  } deriving (Show)

data Maybe a = Just a | Nothing
```
    
