---
layout: post
title: "Image Smoothing Algorithms"
categories: Tech
comments: true
---

During my eternal quest to knowledge, I went accross this article: http://blog.geveo.com/Image-Smoothing-Algorithms

I have a lot of personal projects (I mean, quiiiiiite a lot). So I may experiment a few things and read a lot of technical contents.

Lastly, I wanted to know how image smoothing algorithms work in spite of my poor math knowledge. One (programmer) does not simply speak maths on a daily basis. I’ve even heard that some so-called software developers do hate maths (especially the one who graduaded on Udemy after three months).

Well it’s time to make our hands dirty here, because we are going to explore maths and, above all, **code**.

As I was not satisfied with the work of the person who wrote the article I mentioned above, I will explore on my own what the image smoothing algorithms are all about.

Bear with me and le’t get started.

## A little bit of litterature

In math, there is the notion of “kernel” which can be mistaken with the known kernel mathematical object. In image processing, it’s basically a matrix; but as programmers let’s say **two dimensional array**. As an example :

$$
\begin{equation*}
\begin{bmatrix}
1 & 2 & 3 \\
2 & 1 & 2 \\
3 & 2 & 1
\end{bmatrix}
\end{equation*}
$$

The matrix above is a 3x3 matrix. It’s as if we had a list of lists in Python:

```python
matrix = [[1, 2, 3], [2, 1, 2], [3, 2, 1]]
```

But why are we talking matrixes here? Because pictures are a matrix of pixels.

Let’s take the picture our article took in example:

![Filter me!](/assets/2023-04-02-image-smoothing-algorithms/filter-me.png)

You can observe on this picture that there are a lot of black and white pixels we would like to get rid of. These unwanted pixels are called “noise”, and the image smoothing algorithms we are going to study aims at mitigating (deleting indeed) this noise.

Anyway. Let’s dig into the different algorithms.

## Mode Filter Algorithm

The Mode Filter Algorithm consists in getting the “mode” of the close pixels, then pick this pixel to smooth the image.

And there you go: “what the heck is a mode?”.

In maths (again!), the mode **[of a matrix]** is the term which appears the most in this matrix. That’s as simple as that (and I spent way, way too much time grasping this concept).

See our matrix above? Let me paste it right here:

$$
\begin{equation*}
\begin{bmatrix}
1 & 2 & 3 \\
2 & 1 & 2 \\
3 & 2 & 1
\end{bmatrix}
\end{equation*}
$$

Here, you can see that the term “2” appears four times, whereas the term “1” appears three times and the term “3” appears twice. So the mode of the matrix above is “2”.

And that’s how the mode filter algorithm work!

Now let’s practice a little bit, shall we? Download the picture above (it should be called “filter-me.png”) and get the first three pixels of the very first three rows, at the very top left of the picture. You may use GIMP for that.

What is helpful is that the image is at grayscale, so every level of red, green and blue in a single pixel are indentical.

Here is a screenshot of the pixels I am talking about, while I am extracting them on GIMP:

![The nine first pixels of our picture, as a 3x3 matrix](/assets/2023-04-02-image-smoothing-algorithms/3x3.png)


We have:

$$
\begin{equation*}
\begin{bmatrix}
147 & 100 & 96 \\
147 & 255 & 102 \\
147 & 107 & 0
\end{bmatrix}
\end{equation*}
$$

So what’s our mode going to be here? Well, as you can see, the term “147” appears three times and is the most frequent. So the mode here is “147” and our very first pixel will have the value “147”.

I understand that this is not a relevant example, as our pixel’s grayscale is 147 already. You want a better example?

Let’s take the pixel of the second column and the second row, whose value is 255 (plain white!).

Now, let’s take the pixels around, going to the right and the bottom. Here is our new matrix and, as I feel cool, I even put a number of the pixels I am talking about, eh.


![Other pixels, as a 3x3 matrix, again](/assets/2023-04-02-image-smoothing-algorithms/3x3-2.png)

Our matrix is:

$$
\begin{equation*}
\begin{bmatrix}
255 & 102 & 101 \\
107 & 0 & 105 \\
106 & 107 & 105
\end{bmatrix}
\end{equation*}
$$

Who’s our winner here? Well, we have an *ex æequo* situation, as both the terms “107” and “105” appear twice, so it’s a *bimodal matrix*. It has two modes. Still a bad example? Naaah… I just wanted to illustrate that not only will the value be different from 255, but also definitely far from it, regardless of whether it’s 107 or 105.

In here you can chose either modes we have come up with, so let’s stick with 105.

I hope that you have grasped the concept, so now it is time to write some python script to smooth our image using this mode algorithm thing.

(to be continued…)