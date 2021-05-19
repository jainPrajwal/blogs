# Font Size:em,rem,pixel or percent?

![Font Size](https://www.digitalauthority.me/wp-content/uploads/2019/03/shutterstock_301849946.jpg "Font Size")

I still remember when I was creating my first portfolio site and was trying to make it responsive,even after creating many media queries I wasnt able to get the desired reponsiveness.I was totally frustrated.

And then I came to know it was because I had used font sizes in pixels.

So, my dear friends,I dont want you to waste your valuable time on such simple things like I did!
So do read till the end.

`pixels` (`px`) do not scale.
It is an `absolute` unit.

Whereas `em` , `rem` are `relative/responsive` units.
They scale according to the viewport.

Change in the value of `parent` or `root` element affects the value of relative units.
`em` should be used for padding,margin,line-height etc.

Okay so before studying em and rem,
Remember `default font size of browser is 16px`.

Thus &nbsp;`1rem = 16px by default.`

## USING EM - ELEMENT

>For eg.

<table border="2px" >

<th>Style</th>

<th>Computed style</th>

<tr>

<td style="width:50%;">
html {
    font-size:18px;
}

section {
    font-size:14px;
    padding:3em;
}
</td>
<td style="width:50%;">
html {
    font-size:18px;
}

section {
    font-size:14px;
    padding:42px;
}
</td>
</tr> 
</table>

So independent of font size specified in html element em takes the font size of its local element.
And if font size is not defined in its local element then it checks it parent's element.
This is a part of inheritance in em units.
We shall learn more about inheritance later in this blog.

## USING REM - ROOT ELEMENT 
>For eg.

<table border="2px" >

<th>Style</th>

<th>Computed style</th>

<tr>

<td  style="width:50%;">
html {
    font-size:18px;
}

section {
    font-size:14px;
    padding:3rem;
}
</td>
<td  style="width:50%;">
html {
    font-size:18px;
}

section {
    font-size:14px;
    padding:54px;
}
</td>
</tr> 
</table>

Independent of font size defined in local element it takes the value in the root element i.e. html


### EFFECT OF INHERITANCE ON EM UNITS

Inheritance changes the game in em units and also makes it quite complex.

With em the child element inherits the value of its parent and up to its grandparent.


```html
<section class="wrapper">
    Grandparent
    <div class="container">
        Parent
        <div class="container">
            Child
        </div>
    </div>
</section>
```

<table border="2px">

<th>Style</th>

<th>Computed style</th>

<tr>

<td style="width:50%;">
html {
    font-size:16px;
}

.wrapper {
    font-size:1.5em;
}

.container {
    padding:2em;
}
</td>

<td style="width:80%;">

html {
    font-size:16px;
}

.wrapper {
    font-size:24px;//16 * 1.5//
}

.container {
    padding:48px;//24 * 2 //  
}
</td>
</tr>  
</table>

If we want to override the inherited values then we need to expicitly set the unit element to `px`.

### Stylesheet  

```html
<section class="page-wrapper">
    GrandParent
    //16px
    <div class="container">
        Parent
        //24 * 1.5 = 36px;
        <div class="container">
            Child
            //36 * 1.5 = 54px;
        </div>
    </div>
</section>
```

```css
html {
    font-size: 16px;
}
.page-wrapper {
    font-size:24px;
}

.container {
    font-size:1.5em;
}
```

Here the font size of div with `.container` class is computed based on its parent element.
The interesting thing here is that the parent and child in the HTML above do `not` have the same font size irrespective  of the fact that they share the same class name.

### PERCENT
Use percent specifically when making site responsive.
Also for ease of usage most programmers do the following.

```css
html {
    font-size:62.5%;
}
```

Thus now `1rem = 10px;`  
This makes furhter calculations easier.  

## CONCLUSION

>These are just my personal recommendations based on my research and studies.

1. `em` should be used for padding,margin,line-height etc.
`em` for those elements whose properties shall scale with the changing viewport.  

2. Use `rem` for everything else.

3. For changing viewports, use `%` unit in font size.This makes font size responsive.

>Note:
Guys, I have taken reference of this blog.
[Sizing in CSS: px vs em vs rem](https://chiamakaikeanyi.dev/sizing-in-css-px-vs-em-vs-rem/#:~:text=When%20you%20use%20px%2C%20you,element%20in%20percentage%20is%20recommended.)
This is really a very helpful blog!
Do give it a read for more undertanding.
