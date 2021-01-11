# Introduction to the box model

To design reusable and well behaving components, it is elementary that we understand the HTML box model.
This post will cover the basics to get you started (or refresh what you already know).
For a more in-depth look, check out [this article on MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model).

<style>
    .content {
        background-color: blue;
        width: 128px; 
        height: 64px; 
        display: inline-flex; 
        align-items:center; 
        justify-content: center;
    }

    .padded-content {
        display: inline-flex;
        flex-direction: column;
        align-content:center; 
        justify-content: center;
        background-color: purple;
        padding: 0 32px 32px;
        width: 128px;
    }

    .padded-content__border {
        width: 192px;
        border-color: red;
        border: solid red 8px;
    }

    .padded-content__margin {
        margin: 16px;
    }

    .container {
        background-color: yellow;
        color: black;
        width: 240px;
        display: flex;
    }

    .example {
        background-color: white;
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        border: solid black 1px;
        height: 256px;
    }

    .example-flex {
    }

    .padded-content__label {
        display: inline-flex;
        justify-content: center;
        align-items: center;
        height: 32px;
        width: 100%;
    }
</style>

## The content area

The content area is where the actual content of our element will be displayed. Such content could be anything from simple text to your whole application. The content area will be directly affected by the dimensions (e.g. `width` and `height`) you set in your CSS.

<div class="content">
<p>CONTENT</p>
</div>

## Padding

Padding is part of the element itself. This is used to align the actual content according to design considerations. For example, separating the text of a button from the actual border.
Padding the will not be added towards the total dimensions of your element by default.

In many cases you might want to set the `box-sizing` property of your borders to `border-box`, so the border is considered part of the total size of your element.

_See [box-sizing on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) for some excellent examples_

<div class="padded-content">
    <p class="padded-content__label">PADDING</p>
    <div class="content">CONTENT</div>
</div>

## Borders

Next are borders. This includes the content and padding of our element. Like padding the will not be added towards the total dimensions of your element by default, unless `border-box` is specified differently.

<div class="padded-content__border">
    <div class="padded-content">
        <p class="padded-content__label">PADDING</p>
        <div class="content">CONTENT</div>
    </div>
</div>

## Margin

The margin is the final part of our element. It is not part of the actual element itself, but it will determine where the element is positioned. You can think of it as the distance between your element and it's parent element.

<div class="container">
    <div class="padded-content__margin">
        <div class="padded-content__border">
            <div class="padded-content">
                <p class="padded-content__label">PADDING</p>
                <div class="content">CONTENT</div>
            </div>
        </div>
    </div>
</div>

Now, what does that mean exactly for your applications?
Let's take a look at this example with two elements.

<div class="example">
    <div class="container example-flex">
        <div class="padded-content__margin">
            <div class="padded-content__border">
                <div class="padded-content">
                    <p class="padded-content__label"></p>
                    <div class="content">COMPONENT 1</div>
                </div>
            </div>
        </div>
    </div>
    <div class="container example-flex">
        <div class="padded-content__margin">
            <div class="padded-content__border">
                <div class="padded-content">
                    <p class="padded-content__label"></p>
                    <div class="content">COMPONENT 1</div>
                </div>
            </div>
        </div>
    </div>
</div>

NOTE: _The elements here are aligned with `display: flex`. More on that later._

As you can see, the elements are positioned neatly in the corners, both having a nice margin towards the borders of their container. This will make your customers and designers rejoice!

## Best Practice #1

_'But Toby,'_ you might ask, _'aren't `margin` and `padding` interchangeable?'_

Well, to that I say: _'Absolutely not!'_
You might be able to achieve the same look by using either of those properties on your element. However, you will mess up your `box model` completely, and any changes you want to make in the future will be a huge pain.

Imagine the example above with two elements: If those are buttons, you will want to separate them from the background somehow. Either with a nice `border` if you are stuck in 2005, or by adding a nice background color if you're stuck in 2016.

So, what's the big deal? Well, margins don't have background colors. Good luck trying to color your button when you used a `margin` instead of a `padding`...
