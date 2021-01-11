# Introduction to the box model

To design reusable and well behaving components, it is elementary that we understand the HTML box model.
This post will cover the basics to get you started (or refresh what you already know).
For a more in-depth look, check out [this article on MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model).

## The content area

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
        border: solid black 1px;
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

<div class="content">
<p>CONTENT</p>
</div>

## Padding

Padding is part of the box itself. This is used to align the actual content according to design considerations. For example, separating the text of a button from the actual border.

<div class="padded-content">
    <p class="padded-content__label">PADDING</p>
    <div class="content">CONTENT</div>
</div>

## Borders

Next are borders. This includes the content and padding of our element. Note that you might want to set the `box-sizing` property of your borders to `border-box`, so the border is considered part of the total size of your element.

_See [box-sizing on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) for some excellent examples_

<div class="padded-content__border">
    <div class="padded-content">
        <p class="padded-content__label">PADDING</p>
        <div class="content">CONTENT</div>
    </div>
</div>

## Margin

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

## Example with Components

<div class="example">
    <div class="container example-flex">
        <div class="padded-content__margin">
            <div class="padded-content__border">
                <div class="padded-content">
                    <p class="padded-content__label">PADDING 1</p>
                    <div class="content">CONTENT 1</div>
                </div>
            </div>
        </div>
    </div>
    <div class="container example-flex">
        <div class="padded-content__margin">
            <div class="padded-content__border">
                <div class="padded-content">
                    <p class="padded-content__label">PADDING 2</p>
                    <div class="content">CONTENT 2</div>
                </div>
            </div>
        </div>
    </div>
</div>
