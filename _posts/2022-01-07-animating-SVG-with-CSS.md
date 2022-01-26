---
title: "Animating SVG with CSS"
toc: true
toc_sticky: true
categories:
 - WebDev
 - Code
tags:
 - Graphics design
 - SVG
---
I did a course on Skillshare called ["Creative Coding: Animating SVG with Simple CSS Code"](https://www.skillshare.com/classes/Creative-Coding-Animating-SVG-with-Simple-CSS-Code/1735436116/projects). The course is relatively short (28 minutes) and covers the basics of animating SVG with CSS. I would say it’s aimed at people who already have a foundational understanding in HTML and CSS and want to level up their web development game.

To practice this, I created the SVG below using Illustrator and animated it.

<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 229.77 229.77" height="300px" class="align-center">
  <defs>
    <style>
      .cls-1{fill:#f0be59;}
      .cls-1,.cls-2{stroke:#231f20;}
      .cls-1,.cls-2,.cls-4{stroke-miterlimit:10;}
      .cls-1,.cls-4{stroke-width:3px;}
      .cls-2{fill:#fff;stroke-width:4px;}
      .cls-3{fill:#231f20;}
      .cls-4{fill:none;stroke:#fff;stroke-linecap:round;}
      .eye-center {animation-name: moveEye; animation-duration: 3s; animation-iteration-count: infinite;}
      @keyframes moveEye {20% {transform: translateX(-30px);}60% {transform: translateY(-10px) scale(1.1);}}
    </style>
  </defs><title>eye</title>
    <rect class="cls-1" x="1.5" y="1.5" width="226.77" height="226.77"/>
    <path class="cls-2" d="M191.79,114.72a110.81,110.81,0,0,1-156.81,0A110.81,110.81,0,0,1,191.79,114.72Z" transform="translate(1.5 1.5)"/>
    <g class="eye-center">
      <circle class="cls-3" cx="114.89" cy="114.89" r="24.16"/>
      <path class="cls-4" d="M99.31,104.39c0-4.19,3.74-7.58,8.36-7.58" transform="translate(1.5 1.5)"/>
  </g>
</svg>
<br>

# The SVG

To do this, I inserted the SVG code into the HTML code.

{% highlight html linenos %}
<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 229.77 229.77" height="200px">
  <defs>
    <style>
      .cls-1{fill:#f0be59;}
      .cls-1,.cls-2{stroke:#231f20;}
      .cls-1,.cls-2,.cls-4{stroke-miterlimit:10;}
      .cls-1,.cls-4{stroke-width:3px;}
      .cls-2{fill:#fff;stroke-width:4px;}
      .cls-3{fill:#231f20;}
      .cls-4{fill:none;stroke:#fff;stroke-linecap:round;}
    </style>
  </defs><title>eye</title>
    <rect class="cls-1" x="1.5" y="1.5" width="226.77" height="226.77"/>
    <path class="cls-2" d="M191.79,114.72a110.81,110.81,0,0,1-156.81,0A110.81,110.81,0,0,1,191.79,114.72Z" transform="translate(1.5 1.5)"/>
    <g class="eye-center"> <!--added a <g> element to group the two components -->
      <circle class="cls-3" cx="114.89" cy="114.89" r="24.16"/>
      <path class="cls-4" d="M99.31,104.39c0-4.19,3.74-7.58,8.36-7.58" transform="translate(1.5 1.5)"/>
  </g>
</svg>
{% endhighlight %}

Using the web developer inspector tool, I could see that the SVG consists of four components:

1. The yellow square with the black outline `<rect class="cls-1"...`
2. The white oval with a black outline `<path class="cls-2"...`
3. The black circle  `<circle class="cls-3"...`
4. The white curved line inside the black circle which represents the speck of light `<path class="cls-4"...`

Because I wanted to move the centre of the eye, which consists of components #3 and #4, I had to group these two components together by adding a `<g>` element in **lines 15 and 18**.

# Editing the CSS code

This is the CSS code I used to animate my SVG. I could add this CSS code on a separate CSS file or within the `<style>` element in the SVG code.

{% highlight css linenos %}
.eye-center {
  animation-name: moveEye;
  animation-duration: 3s;
  animation-iteration-count: infinite;
}

@keyframes moveEye {
  20% {
    transform: translateX(-30px);
  }
  60% {
    transform: translateY(-10px) scale(1.1);
  }

}
{% endhighlight %}

To define the animation in CSS, we use @keyframes followed by the given name of the animation, which in this case is `@keyframes moveEye`.  The progress of the animation is defined using percentages. For this animation, I wanted to move (i.e. translate) and change the size (i.e. scale) of the centre of the eye. This can be done using the `transform` property.

Finally, I created a class called `eye-center`[^1] and assigned it to the `<g>` element in the SVG code. This class consists of the animation name, how long one animation cycle should last, and how many cycles should be done.

# Replacing the preloader of a website

So one of my side projects is developing and maintaining a [symposium website](http://monash-sciencesymposium.com/). I created it from this [Jekyll-based conference website](https://github.com/gdg-x/zeppelin) which has an animated preloader. Armed with my newfound knowledge, I decided it was time I replaced the original preloader with an animation of the symposium’s logo pulsating.

<br>
<style>
  .loading-logo{animation-name:pulse;animation-duration:1s;animation-iteration-count:infinite}@keyframes pulse{50%{transform:scale(1.3)}}
</style>
<svg id="Layer_1" class="loading-logo align-center" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 95 60" height="80px">
    <defs>
      <style>.cls-5{fill:#00599d;}.cls-6{fill:#2e3192;}.cls-7{fill:#65c8d0;}.cls-8{fill:#d4145a;}.cls-9,.cls-10{fill:none;stroke-miterlimit:10;}.cls-9{stroke:#d4145a;stroke-width:6px;}.cls-10{stroke:#00599d;stroke-width:4px;}
      </style>
    </defs><title>MSS_logo</title>
      <path class="cls-5" d="M35.1,12.61l-4.6,8.8a48.43,48.43,0,0,0-5.29-8.61c-1.73-2-3.55-3.08-5.82-3.08s-4.2,1.15-6,3.24V2.69a14.53,14.53,0,0,1,6-1.22,14.56,14.56,0,0,1,5.82,1.16C29.43,4.44,32.6,8.41,35.1,12.61Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-5" d="M87.17,2.5v9.36a6.72,6.72,0,0,0-5.51-2.14c-2.47,0-4.42,1.29-6.28,3.63A58.44,58.44,0,0,0,69.78,23c-4.19,8.37-8.93,17.85-19.26,17.85-8,0-12.64-5.67-16.26-12.1L38.87,20c3.88,7.67,7,12.61,11.65,12.61,4.88,0,7.74-5,11.88-13.28,3.22-6.45,6.78-13.57,13-16.49a14.46,14.46,0,0,1,6.28-1.36A14.66,14.66,0,0,1,87.17,2.5Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-5" d="M25.21,5.06V30.39a8.79,8.79,0,0,1-6.3,2.8,8.4,8.4,0,0,1-5.49-2.08v-26Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-5" d="M18.91,40.27a12.58,12.58,0,0,0,6.3-1.63V61.47H13.42V39.06A12.65,12.65,0,0,0,18.91,40.27Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-6" d="M25.21,31.57v5.89a12.58,12.58,0,0,1-6.3,1.63,12.65,12.65,0,0,1-5.49-1.21V32.29a8.4,8.4,0,0,0,5.49,2.08A8.79,8.79,0,0,0,25.21,31.57Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-5" d="M87.17,13.63V30.69a8.66,8.66,0,0,1-6,2.5,8.53,8.53,0,0,1-5.8-2.34V15.11c1.86-2.33,3.81-4.21,6.28-4.21A7.33,7.33,0,0,1,87.17,13.63Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-5" d="M81.18,40.27a12.66,12.66,0,0,0,6-1.46V61.47H75.38V38.9A12.57,12.57,0,0,0,81.18,40.27Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-6" d="M87.17,31.87v5.76a13,13,0,0,1-11.79.09V32a8.58,8.58,0,0,0,5.8,2.34A8.66,8.66,0,0,0,87.17,31.87Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-7" d="M64.33,13.68l-2.62,5C58.67,12.94,55.27,8,50.05,8c-6.33,0-9.79,6.92-13.46,14.26-2.93,5.86-6.15,12.3-11.38,15.24a12.58,12.58,0,0,1-6.3,1.63,12.65,12.65,0,0,1-5.49-1.21V32.29a8.4,8.4,0,0,0,5.49,2.08,8.79,8.79,0,0,0,6.3-2.8c2.77-2.69,4.93-7,7.16-11.46,4-7.91,8.44-16.87,17.68-16.87C56.79,3.24,61,8,64.33,13.68Z" transform="translate(-5.18 -1.47)"/>
      <path class="cls-7" d="M87.17,31.87v5.76a13,13,0,0,1-11.79.09c-3.29-1.67-5.8-4.7-7.92-8.16l2.61-5c1.57,2.89,3.33,5.72,5.31,7.45a8.58,8.58,0,0,0,5.8,2.34A8.66,8.66,0,0,0,87.17,31.87Z" transform="translate(-5.18 -1.47)"/>
      <circle class="cls-8" cx="87.33" cy="8" r="4.13"/>
      <circle class="cls-5" cx="92.56" cy="13.79" r="2.36"/>
      <circle class="cls-8" cx="4.66" cy="32.7" r="2.36"/>
      <line class="cls-6" x1="17.08" y1="57.95" x2="17.08" y2="60"/>
      <line class="cls-6" x1="79.63" y1="57.95" x2="79.63" y2="60"/>
      <circle class="cls-8" cx="1.47" cy="28.99" r="1.47"/>
  </svg>
  <br>

# Future Learning

I found this [informative article](https://blog.logrocket.com/animating-svg-with-css-83e8e27d739c/) that talks a bit more in-depth about animating SVG with CSS code. I'm looking forward to creating hover animations.

[^1]: The only you'll ever see me use American spelling is when I’m writing code.
