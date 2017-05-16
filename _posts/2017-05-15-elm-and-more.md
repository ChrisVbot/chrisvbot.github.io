---
layout: single
author_profile: true
title: Elm Talk
---

I've recently created a short course as an intro to Elm at my job and I found the language to be really interesting and pretty nice to work with. As a quick intro, [Elm](http://elm-lang.org/) is a statically-typed, functional language created by Evan Czaplicki and released in 2012. It compiles to JavaScript, and also has some great built-in tooling including a development server, package manager, and a really great compiler. In fact, one of the key features mentioned on the Elm site is the fact that Elm does not produce runtime exceptions in practice. Instead, the compiler will give you a (usually) understandable error message that is actually pretty friendly. That means no more null or undefined errors - pretty cool! 

Here's an example of a function with static typing:

```elm
add : Int -> Int -> Int
add x y =
    x + y
```

The function is named 'add' and takes two parameters, 'x' and 'y.' Above that, we are explicitly telling Elm what types to expect, and what type we are returning. No need to explicitly use the 'return' keyword either. 

Coding in a functional language that emphasises static types and immutability definitely took a bit of getting used to, especially coming from the more loosey-goosey world of JavaScript. I was glad to have had some experience with Redux (which actually takes [some inspiration](http://redux.js.org/docs/introduction/PriorArt.html) from Elm) since they share many of the same concepts such as a focus on pure functions, immutability, and having a centralized state. The benefit of using Elm in contrast to creating a JavaScript app with, say, React/Redux is that Elm is a language unto itself, which means that in a lot of cases, it has the functionality you may be seeking right out of the box. So, rather than worrying about all the different JavaScript libraries and tools in a given project, you can instead just use the built-in core Elm features. For example, a simple app that takes in a user input and just updates the DOM on the fly is pretty trivial to write in Elm (note that comments are written with either -- or between {-- --} if multiline): 

```elm
import Html exposing (Html, Attribute, div, input, text)
import Html.Attributes exposing (..)
import Html.Events exposing (onInput)


main =
    Html.beginnerProgram 
        { model = model, view = view, update = update }


-- MODEL

type alias Model =
    { content : String }


{-- 
This is our model which will keep track of whatever 
text user types into the field
--}
model : Model
model =
    { content = "" }


-- UPDATE

{--
In this app there is only one kind of message. The 
user can change the contents of the text field
and it will always be a string
--}
type Msg
    = Change String


update : Msg -> Model -> Model
update msg model =
    case msg of
        {--
        only have to handle one case because 
        there's only one kind of message
        --}
        Change newContent ->
            --record update syntax
            { model | content = newContent }


-- VIEW
{--
here we are saying how to view our application
--}

view : Model -> Html Msg
view model =
    --creating a div with two children
    div []
        [ input [ placeholder "Text to reverse", onInput Change ] []
        , div [] [ text model.content ]
        ]
```
Now, this would be pretty easy to recreate in React or even vanilla JS, but Elm takes care of state management for us without any external libraries. Any updates to the state (defined in the 'model' function) actually return new versions of the model, rather than mutating the original state. Also note that basically everything is a function, including the HTML attributes! We could write those like the following: 

```elm
div [ style [ ("fontSize", "2em") ] ][ text "Hello!" ]
```
We actually have a number of functions here, all of which are imported with the Html module: div, style, and text. Here, we are creating inline styles just like in React. If we wanted to, we could extract that out into a separate function as well. Really, it's functions all the way down. 

Like any language, Elm has its ups and downs. On the downside, I find the documentation tends to be difficult to understand for beginners to functional programming, JSON decoding is not easy, and many of the examples in the official docs are overly simple. That said, I think it's worth checking out and I'm very curious to see where it goes in the future. [Here's](https://github.com/ChrisVbot/simple-elm-project) my Github repo with some simple examples. For more reading, [this article](https://medium.com/@rgoomar/why-i-think-elm-is-the-future-of-front-end-development-21e9b091fa05) by Rishi Goomar does a great job of summing up some of the cool features of Elm. I would definitely recommend giving it a try! 







