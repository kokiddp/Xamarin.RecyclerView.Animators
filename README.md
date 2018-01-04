Xamarin bindings for RecyclerView Animators
======================
Original Java Library: https://github.com/wasabeef/recyclerview-animators

<p align="center">
  <img src="https://github.com/wasabeef/recyclerview-animators/raw/master/art/logo.jpg" width="80%">
</p>

[![NuGet](https://img.shields.io/nuget/dt/Xamarin.RecyclerView.Animators.svg)](https://www.nuget.org/packages/Xamarin.RecyclerView.Animators)
[![NuGet](https://img.shields.io/nuget/v/Xamarin.RecyclerView.Animators.svg)](https://www.nuget.org/packages/Xamarin.RecyclerView.Animators)
[![License](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)

RecyclerView Animators is an Android library that allows developers to easily create RecyclerView with animations.

Please feel free to use this.

# Features

* Animate addition and removal of `ItemAnimator`
* Appearance animations for items in `RecyclerView.Adapter`

# Demo

### ItemAnimator
<img src="https://github.com/wasabeef/recyclerview-animators/raw/master/art/demo.gif" width="32%"> <img src="https://github.com/wasabeef/recyclerview-animators/blob/master/art/demo2.gif" width="32%"> <img src="https://github.com/wasabeef/recyclerview-animators/raw/master/art/demo3.gif" width="32%">

### Adapters
<img src="https://github.com/wasabeef/recyclerview-animators/blob/master/art/demo4.gif" width="32%"> <img src="https://github.com/wasabeef/recyclerview-animators/blob/master/art/demo5.gif" width="32%">

# How do I use it?

## Setup

#### Nuget

install via Package Manager
> PM> Install-Package Xamarin.RecyclerView.Animators

or search for it in Manage NuGet Packages in Visual Studio

#### Namespace
import the namespace

```c#
using JP.Wasabeef.Recyclerview.Adapters;
```

## ItemAnimator
### Step 1

Set RecyclerView ItemAnimator.

```c#
RecyclerView recyclerView = FindViewById<RecyclerView>(R.id.list);
recyclerView.SetItemAnimator(new SlideInLeftAnimator());
```

```c#
RecyclerView recyclerView = FindViewById<RecyclerView>(R.id.list);
SlideInUpAnimator animator = new SlideInUpAnimator(new OvershootInterpolator());
recyclerView.SetItemAnimator(animator);
```

## Step 2
Please use the following  
`NotifyItemChanged(int)`  
`NotifyItemInserted(int)`  
`NotifyItemRemoved(int)`  
`NotifyItemRangeChanged(int, int)`  
`NotifyItemRangeInserted(int, int)`  
`NotifyItemRangeRemoved(int, int)`  

> If you want your animations to work, do not rely on calling `NotifyDataSetChanged()`; 
> as it is the RecyclerView's default behavior, animations are not triggered to start inside this method.

```c#
public void Remove(int position) {
  mDataSet.Remove(position);
  NotifyItemRemoved(position);
}

public void Add(string text, int position) {
  mDataSet.Add(position, text);
  NotifyItemInserted(position);
}
```

### Advanced Step 3

You can change the durations.

```c#
recyclerView.GetItemAnimator().SetAddDuration(1000);
recyclerView.GetItemAnimator().SetRemoveDuration(1000);
recyclerView.GetItemAnimator().SetMoveDuration(1000);
recyclerView.GetItemAnimator().SetChangeDuration(1000);
```

### Advanced Step 4

Change the interpolator.

```c#
SlideInLeftAnimator animator = new SlideInLeftAnimator();
animator.SetInterpolator(new OvershootInterpolator());
recyclerView.SetItemAnimator(animator);
```


### Animators

#### Cool
`LandingAnimator`

##### Scale
`ScaleInAnimator`, `ScaleInTopAnimator`, `ScaleInBottomAnimator`  
`ScaleInLeftAnimator`, `ScaleInRightAnimator`

##### Fade
`FadeInAnimator`, `FadeInDownAnimator`, `FadeInUpAnimator`  
`FadeInLeftAnimator`, `FadeInRightAnimator`

##### Flip
`FlipInTopXAnimator`, `FlipInBottomXAnimator`  
`FlipInLeftYAnimator`, `FlipInRightYAnimator`

##### Slide
`SlideInLeftAnimator`, `SlideInRightAnimator`, `OvershootInLeftAnimator`, `OvershootInRightAnimator`  
`SlideInUpAnimator`, `SlideInDownAnimator`

## RecyclerView.Adapter
### Step 1

Set RecyclerView ItemAnimator.

```c#
RecyclerView recyclerView = FindViewById<RecyclerView>(R.id.list);
MyAdapter adapter = new MyAdapter();
recyclerView.SetAdapter(new AlphaInAnimationAdapter(adapter));
```

### Advanced Step 2

Change the durations.

```c#
MyAdapter adapter = new MyAdapter();
AlphaInAnimationAdapter alphaAdapter = new AlphaInAnimationAdapter(adapter);
alphaAdapter.SetDuration(1000);
recyclerView.SetAdapter(alphaAdapter);
```

### Advanced Step 3

Change the interpolator.

```c#
MyAdapter adapter = new MyAdapter();
AlphaInAnimationAdapter alphaAdapter = new AlphaInAnimationAdapter(adapter);
alphaAdapter.SetInterpolator(new OvershootInterpolator());
recyclerView.SetAdapter(alphaAdapter);
```

### Advanced Step 4

Disable the first scroll mode.

```c#
MyAdapter adapter = new MyAdapter();
AlphaInAnimationAdapter alphaAdapter = new AlphaInAnimationAdapter(adapter);
scaleAdapter.SetFirstOnly(false);
recyclerView.SetAdapter(alphaAdapter);
```

### Advanced Step 5

Multiple Animations

```c#
MyAdapter adapter = new MyAdapter();
AlphaInAnimationAdapter alphaAdapter = new AlphaInAnimationAdapter(adapter);
recyclerView.SetAdapter(new ScaleInAnimationAdapter(alphaAdapter));
```

### Adapters

#### Alpha
`AlphaInAnimationAdapter`

#### Scale
`ScaleInAnimationAdapter`

#### Slide
`SlideInBottomAnimationAdapter`  
`SlideInRightAnimationAdapter`, `SlideInLeftAnimationAdapter`


Developed By
-------
Daichi Furiya (Wasabeef) - <dadadada.chop@gmail.com>

Xamarin bindings by Gabriele Coquillard (kokiddp) - <gabriele.coquillard@gmail.com>


Contributions
-------

Any contributions are welcome!


License
-------

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
