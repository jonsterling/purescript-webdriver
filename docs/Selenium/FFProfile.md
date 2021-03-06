## Module Selenium.FFProfile

#### `FFPreference`

``` purescript
data FFPreference :: *
```

#### `FFProfileBuild`

``` purescript
newtype FFProfileBuild a
```

##### Instances
``` purescript
Functor FFProfileBuild
Apply FFProfileBuild
Bind FFProfileBuild
Applicative FFProfileBuild
Monad FFProfileBuild
```

#### `setPreference`

``` purescript
setPreference :: String -> FFPreference -> FFProfileBuild Unit
```

#### `setStringPreference`

``` purescript
setStringPreference :: String -> String -> FFProfileBuild Unit
```

#### `setIntPreference`

``` purescript
setIntPreference :: String -> Int -> FFProfileBuild Unit
```

#### `setNumberPreference`

``` purescript
setNumberPreference :: String -> Number -> FFProfileBuild Unit
```

#### `setBoolPreference`

``` purescript
setBoolPreference :: String -> Boolean -> FFProfileBuild Unit
```

#### `buildFFProfile`

``` purescript
buildFFProfile :: forall e. FFProfileBuild Unit -> Aff (selenium :: SELENIUM | e) Capabilities
```

#### `intToFFPreference`

``` purescript
intToFFPreference :: Int -> FFPreference
```

#### `numberToFFPreference`

``` purescript
numberToFFPreference :: Number -> FFPreference
```

#### `stringToFFPreference`

``` purescript
stringToFFPreference :: String -> FFPreference
```

#### `boolToFFPreference`

``` purescript
boolToFFPreference :: Boolean -> FFPreference
```


