# Making UI elements fit the size of their content

Normally when positioning a UI element with its Rect Transform, its position and size is specified manually (optionally including behavior to stretch with the parent Rect Transform).

通常当 UI 元素定位到 Rect Transform 上时，其位置和大小是手动指定的 （选项包括 stretch 与父 Rect Transform）。

However, sometimes you may want the rectangle to be automatically sized to fit the content of the UI element. This can be done by adding a component called Content Size Fitter.

然而，有时你可能想要矩形可以自动调整大小来适应 UI 元素的内容。这可以通过添加 一个称为 Content Size Fitter 的组件。

##Fit to size of Text

In order to make a Rect Transform with a Text component on it fit the text content, add a Content Size Fitter component to the same Game Object which has the Text component. Then set both the Horizontal Fit and Vertical Fit dropdowns to the Preferred setting.

为了使 Rect Transform 与 Text 文本组件适合它的的文本内容，添加 Content Size Fitter 组件到具有 Text 文本组件的同一游戏对象上。然后设置 Horizontal Fit、Vertical Fit，或者两个 都预先设置

###How does it work?

What happens here is that the Text component functions as a Layout Element that can provide information about how big its minimum and preferred size is. In a manual layout this information is not used. A Content Size Fitter is a type of Layout Controller, which listens to layout information provided by Layout Elements and control the size of the Rect Transform according to this.

发生了什么在这里是 Text 组件功能作为一个 Layout Element 布局元素，可以提供有关其 最小值和首选的大小是多少的信息。在手动布局中不使用此信息。Content Size Fitter 是 Layout Controller 的一种类型，它听布局信息提供的布局元素和控件的 Rect Transform 大小。 

###Remember the pivot

When UI elements are automatically resized to fit their content, you should pay extra attention to the pivot of the Rect Transform. The pivot will stay in place when the element is resized, so by setting the pivot position you can control in which direaction the element will expand or shrink. For example, if the pivot is in the center, then the element will expand equally in all directions, and if the pivot is in the upper left corner, then the element will expand to the right and down.

当 UI 元素将自动调整大小以适合其内容时，你要额外留意到 pivot 的 Rect Transform。 pivot 留在的地方，当调整元素大小，所以通过设置 pivot 的位置你可以控制哪些内件中元素 将会扩展或收缩。例如，如果 pivot 是在中心，然后该元素将展开同样在所有方向上，如果 pivot 是在左上角，然后该元素将展开向右和向下。

##Fit to size of UI element with child Text

If you have a UI element, such as a Button, that has a background image and a child Game Object with a Text component on it, you probably want the whole UI element to fit the size of the text - maybe with some padding.

如果您有一个用户界面元素如按钮，对它有背景图像和文本组件一个孩子的游戏对象， 你可能想要整个的 UI 元素，以适应文本-也许与一些边距的大小。 

In order to do this, first add a Horizontal Layout Group to the UI element, then add a Content Size Fitter too. Set the Horizontal Fit, the Vertical Fit, ot both to the Preferred setting. You can add and tweak padding using the padding property in the Horizontal Layout Group.

为了做到这一点，首先 Horizontal Layout Group 水平布局组添加到 UI 元素，然后也添 加 Content Size Fitter。设置水平适合、垂直适合，这两个的首选设置。您可以添加和调整填 充使用 padding 属性 Horizontal Layout Group 水平的布局组中

Why use a Horizontal Layout Group? Well, it could have been a Vertical Layout Group as well - as long as there is only a single child, they produce the same result.

为什么要使用一个 Horizontal Layout Group 水平布局组？嗯，可能是一个垂直的布局组 以及-只要还有只有一个孩子，他们产生相同的结果

###How does it work?

The Horizontal (or Vertical) Layout Group functions both as a Layout Controller and as a Layout Element. First it listens to the layout information provided by the children in the group - in this case the child Text. Then it determines how large the group must be (at minimum, and preferrably) in order to be able to contain all the children, and it functions as a Layout Element that provides this information about its minimum and preferred size.

Horizontal (or Vertical) Layout Group 水平 （或垂直） 布局组功能作为一种 Layout Controller 布局控制器和 Layout Element 布局元素。它第一次听由组中的子对象提供的布局 信息-在这种情况下子对象文本。然后，它确定如何大组必须为了能包含所有的孩子，和一 个 Layout Element 布局元素，提供有关其最小值和首选的大小这信息作为它的功能。

The Content Size Fitter listens to layout information provided by any Layout Element on the same Game Object - in this case provided by the Horizontal (or Vertical) Layout Group. Depending on its settings, it then controls the size of the Rect Transform based on this information.

Content Size Fitter 听由任何布局元素相同的游戏对象提供的布局信息-在这种情况下提 供的 Horizontal (or Vertical) Layout Group。然后，根据其设置，这个控件的 Rect Transform 大 小基于此信息的。

Once the size of the Rect Transform has been set, the Horizontal (or Vertical) Layout Group makes sure to position and size its children according to the available space. See the page about the Horizontal Layout Group for more information about how it controls the positions and sizes of its children.

一旦设置 Rect Transform 的大小，Horizontal (or Vertical) Layout Group 水平（或垂直）布
局组可确保在位置和大小，其子对象根据可用空间。看到的水平布局组的有关如何控制位置 和它的孩子大小的详细信息的页面。 

##Make children of a Layout Group fit their respective sizes

If you have a Layout Group (horizontal or vertical) and want each of the UI elements in the group to fit their respective content, what do you do?

如果你有一个布局组 （水平或垂直），想每个 UI 元素组以适合其各自的内容中，你会 做什么？

You can’t put a Content Size Fitter on each child. The reason is that the Content Size Fitter wants control over its own Rect Transform, but the parent Layout Group also wants control over the child Rect Transform. This creates a conflict and the result is undefined behavior.

对每个子对象，你不能把 Content Size Fitter。原因是 Content Size Fitter 想控制控件自己 超出 Rect Transform 的内容，但父布局组想要控制超出子对象 Rect Transform。这会产生冲 突，结果是未定义的行为

However, it isn’t necessary either. The parent Layout Group can already make each child fit the size of the content. What you need to do is to disable the Child Force Expand toggles on the Layout Group. If the children are themselves Layout Groups too, you may need to disable the Child Force Expand toggles on those too.

然而，它也不必要。parent 布局组已经可以使每个 child 适合内容的大小。你需要做的 是将布局元素组件添加到每个 child，Flexible Width 和 Flexible Height 的属性设置为 0。 

Once the children no longer expand with flexible width, their alignment can be specified in the Layout Group using the Child Alignment setting.

你看，在默认情况下布局元素将扩大以填充额外的可用空间。为了防止他们的这，布局 元素组件可以被添加，在哪里可以重写的设置 Flexible Width and Height。 

What if you want some of the children to expand to fill additional available space, but not the other children? You can easily control this by adding a Layout Element component to the children you want to expand and enabling the Flexible Width or Flexible Height properties on those Layout Elements. The parent Layout Group should still have the Child Force Expand toggles disabled, otherwise all the children will expand flexibly.

一旦子对象不再扩大与 flexible width，可以使用的 Child Alignment 子对齐方式设置的布 局组中指定其对齐方式。

###How does it work?

A Game Object can have multiple components that each provide layout information about minimum, preferred and flexible sizes. A priority system determines which values take effect over others. The Layout Element component has a higher priority than the Text, Image, and Layout Group components, so it can be used to override any layout information values they provide.

一个游戏对象可以有多个组件每个提供有关 minimum 最小的、 preferred 首选的和 flexible 灵活的大小的布局信息。优先权制度确定哪些值接管别人的影响。布局元素组件具 有更高的优先级比文本、 图像和布局组组件，所以它可以用来重写它们提供任何布局信息 值。 

When the Layout Group listens to the layout information provided by the children, it will take the overridden flexible sizes into account. Then, when controlling the sizes of the children, it will not make them any bigger than their preferred sizes. However, if the Layout Group has the Child Force Expand option enabled, it will always make the flexible sizes of all the children be at least 1.

当布局组听子对象所提供的布局信息时，它将会考虑重写的 flexible 灵活大小 （它已设 置为 0）。然后，当控制孩子的大小，它不会他们任何大于其首选大小

##More information

This page has explained solutions to a few common use cases. For a more in depth explanation of the auto layout system, see the UI Auto Layout page.