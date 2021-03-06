## Module Selenium

#### `get`

``` purescript
get :: forall e. Driver -> String -> Aff (selenium :: SELENIUM | e) Unit
```

Go to url

#### `wait`

``` purescript
wait :: forall e. Aff (selenium :: SELENIUM | e) Boolean -> Int -> Driver -> Aff (selenium :: SELENIUM | e) Unit
```

Wait until first argument returns 'true'. If it returns false an error will be raised

#### `quit`

``` purescript
quit :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Unit
```

Finalizer

#### `byClassName`

``` purescript
byClassName :: forall e. String -> Aff (selenium :: SELENIUM | e) Locator
```

#### `byCss`

``` purescript
byCss :: forall e. String -> Aff (selenium :: SELENIUM | e) Locator
```

#### `byId`

``` purescript
byId :: forall e. String -> Aff (selenium :: SELENIUM | e) Locator
```

#### `byName`

``` purescript
byName :: forall e. String -> Aff (selenium :: SELENIUM | e) Locator
```

#### `byXPath`

``` purescript
byXPath :: forall e. String -> Aff (selenium :: SELENIUM | e) Locator
```

#### `affLocator`

``` purescript
affLocator :: forall e. (Element -> Aff (selenium :: SELENIUM | e) Element) -> Aff (selenium :: SELENIUM | e) Locator
```

Build locator from asynchronous function returning element.
I.e. this locator will find first visible element with `.common-element` class
```purescript
affLocator \el -> do
  commonElements <- byCss ".common-element" >>= findElements el
  flagedElements <- traverse (\el -> Tuple el <$> isVisible el) commonElements
  maybe err pure $ foldl foldFn Nothing flagedElements
  where
  err = throwError $ error "all common elements are not visible"
  foldFn Nothing (Tuple el true) = Just el
  foldFn a _ = a
```

#### `showLocator`

``` purescript
showLocator :: Locator -> String
```

#### `findExact`

``` purescript
findExact :: forall e. Driver -> Locator -> Aff (selenium :: SELENIUM | e) Element
```

#### `childExact`

``` purescript
childExact :: forall e. Element -> Locator -> Aff (selenium :: SELENIUM | e) Element
```

#### `findElement`

``` purescript
findElement :: forall e. Driver -> Locator -> Aff (selenium :: SELENIUM | e) (Maybe Element)
```

Tries to find an element starting from `document`; will return `Nothing` if there
is no element can be found by locator

#### `loseElement`

``` purescript
loseElement :: forall e. Driver -> Locator -> Aff (selenium :: SELENIUM | e) Unit
```

Tries to find element and throws an error if it succeeds.

#### `findElements`

``` purescript
findElements :: forall e f. (Unfoldable f) => Driver -> Locator -> Aff (selenium :: SELENIUM | e) (f Element)
```

Finds elements by locator from `document`

#### `findChild`

``` purescript
findChild :: forall e. Element -> Locator -> Aff (selenium :: SELENIUM | e) (Maybe Element)
```

Same as `findElement` but starts searching from custom element

#### `findChildren`

``` purescript
findChildren :: forall e f. (Unfoldable f) => Element -> Locator -> Aff (selenium :: SELENIUM | e) (f Element)
```

Same as `findElements` but starts searching from custom element

#### `setFileDetector`

``` purescript
setFileDetector :: forall e. Driver -> FileDetector -> Aff (selenium :: SELENIUM | e) Unit
```

#### `navigateBack`

``` purescript
navigateBack :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Unit
```

#### `navigateForward`

``` purescript
navigateForward :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Unit
```

#### `refresh`

``` purescript
refresh :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Unit
```

#### `navigateTo`

``` purescript
navigateTo :: forall e. String -> Driver -> Aff (selenium :: SELENIUM | e) Unit
```

#### `getCurrentUrl`

``` purescript
getCurrentUrl :: forall e. Driver -> Aff (selenium :: SELENIUM | e) String
```

#### `getTitle`

``` purescript
getTitle :: forall e. Driver -> Aff (selenium :: SELENIUM | e) String
```

#### `executeStr`

``` purescript
executeStr :: forall e. Driver -> String -> Aff (selenium :: SELENIUM | e) Foreign
```

Executes javascript script from `String` argument.

#### `sendKeysEl`

``` purescript
sendKeysEl :: forall e. String -> Element -> Aff (selenium :: SELENIUM | e) Unit
```

#### `clickEl`

``` purescript
clickEl :: forall e. Element -> Aff (selenium :: SELENIUM | e) Unit
```

#### `getCssValue`

``` purescript
getCssValue :: forall e. Element -> String -> Aff (selenium :: SELENIUM | e) String
```

#### `getAttribute`

``` purescript
getAttribute :: forall e. Element -> String -> Aff (selenium :: SELENIUM | e) (Maybe String)
```

Tries to find an element starting from `document`; will return `Nothing` if there
is no element can be found by locator

#### `getText`

``` purescript
getText :: forall e. Element -> Aff (selenium :: SELENIUM | e) String
```

#### `isDisplayed`

``` purescript
isDisplayed :: forall e. Element -> Aff (selenium :: SELENIUM | e) Boolean
```

#### `isEnabled`

``` purescript
isEnabled :: forall e. Element -> Aff (selenium :: SELENIUM | e) Boolean
```

#### `getInnerHtml`

``` purescript
getInnerHtml :: forall e. Element -> Aff (selenium :: SELENIUM | e) String
```

#### `getSize`

``` purescript
getSize :: forall e. Element -> Aff (selenium :: SELENIUM | e) Size
```

#### `getLocation`

``` purescript
getLocation :: forall e. Element -> Aff (selenium :: SELENIUM | e) Location
```

#### `clearEl`

``` purescript
clearEl :: forall e. Element -> Aff (selenium :: SELENIUM | e) Unit
```

Clear `value` of element, if it has no value will do nothing.
If `value` is weakly referenced by `virtual-dom` (`purescript-halogen`)
will not work -- to clear such inputs one should use direct signal from
`Selenium.ActionSequence`

#### `takeScreenshot`

``` purescript
takeScreenshot :: forall e. Driver -> Aff (selenium :: SELENIUM | e) String
```

Returns png base64 encoded png image

#### `saveScreenshot`

``` purescript
saveScreenshot :: forall e. String -> Driver -> Aff (selenium :: SELENIUM | e) Unit
```

Saves screenshot to path

#### `getWindow`

``` purescript
getWindow :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Window
```

#### `getWindowPosition`

``` purescript
getWindowPosition :: forall e. Window -> Aff (selenium :: SELENIUM | e) Location
```

#### `getWindowSize`

``` purescript
getWindowSize :: forall e. Window -> Aff (selenium :: SELENIUM | e) Size
```

#### `maximizeWindow`

``` purescript
maximizeWindow :: forall e. Window -> Aff (selenium :: SELENIUM | e) Unit
```

#### `setWindowPosition`

``` purescript
setWindowPosition :: forall e. Location -> Window -> Aff (selenium :: SELENIUM | e) Unit
```

#### `setWindowSize`

``` purescript
setWindowSize :: forall e. Size -> Window -> Aff (selenium :: SELENIUM | e) Unit
```

#### `getWindowScroll`

``` purescript
getWindowScroll :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Location
```

#### `getWindowHandle`

``` purescript
getWindowHandle :: forall e. Driver -> Aff (selenium :: SELENIUM | e) WindowHandle
```

#### `getAllWindowHandles`

``` purescript
getAllWindowHandles :: forall f e. (Unfoldable f) => Driver -> Aff (selenium :: SELENIUM | e) (f WindowHandle)
```

#### `switchTo`

``` purescript
switchTo :: forall e. WindowHandle -> Driver -> Aff (selenium :: SELENIUM | e) Unit
```

#### `close`

``` purescript
close :: forall e. Driver -> Aff (selenium :: SELENIUM | e) Unit
```


