# OH: General Questions, Actions, and Outlets

Hi everyone,

Thanks for attending office hours earlier today (Tuesday, March 10) about the
Nanodegree program in general, actions, and outlets.

If you missed it, you can get to it by navigating [here][hangout].

Here's what Miriam, Eden, Chrisna, and Gabrielle covered:

## The Nanodegree Program

If you haven't seen your [Nanodegree portal][portal] yet, you should take a
look!

We took some questions:

> Should we join Apple's iOS Developer Program? Does Udacity belong to Apple's
> iOS Developer University Program?

It's probably a good idea because joining the program will give you the ability
to have your creations on the App Store and test them on your devices but it is
not required to finish the Nanodegree program. We don't belong to the iOS
university program.

> Is there a printable list of lessons, courses, etc. that we should watch and
> an approximate timeline? That would be very helpful.

We'll get one up to the site hopefully by the end of the week!

> Can someone with no tech job experience and no degree/certificate in anything
> tech/coding related have a decent shot at being hired as an iOS Developer
> after taking this Nanodegree? I have some HTML skills but no other
> programming languages whatsoever.

Yes, we think so. If you put the time in and are serious about it, you will
have multiple, demonstrable examples of your newfound skills.

> Is it possible to add real (not YouTube-generated) subtitles to the videos?

We are in the process of putting them up for the orientation videos. They
should be there soon.

> This isn't really code related, but how long after we submit projects do we
> get them back? I've been waiting almost a week yet I've seen coaches on chat
> say it's usually within 24 hrs?

The number of submissions for the first project was a little surprising to us,
so we're catching up on our backlog. If you've been waiting almost a week, you
should receive an evaluation very shortly.

> I might know the concepts and the hierarchy of the app sequence in my mind
> but don't know how to write down the syntax! Is there any common approach to
> proceed with?

Practice helps a lot. This is something that everyone has trouble with at the
beginning, but, as we gain experience, we become more comfortable. Also note
that knowing every single detail about syntax is not something that
professional developers do. Instead, developers are very good at parsing
through documentation to piece together their logic in code.

> In lesson two of Intro to iOS Development, when we were asked to add the Stop
> Record button, I set the Image Set to use vector images. The instructor did
> it differently. Do I need to change my implementation before submitting my
> project?

Nope! As long as the project meets all of the specifications in the rubric,
your solution does not have to match the instructor's solution exactly.

> Are the TDD or BDD development approaches used in the Nanodegree?

Neither approach is discussed very much in the Nanodegree but we hope to add
resources about testing and debugging in the near future.

## Actions and Outlets

Eden and Chrisna did a demo!

### Introduction

### Actions

You can find the code that Chrisna went through [here][actions]. He went ahead
and commented it with some (hopefully) helpful information and made all of the
functions private.

In the demo, we went over the following topics:

- What you get by default when making an action from the storyboard
- When to use no arguments, when to use sender, and when to use sender and
  event: basically, if you don't need to use sender (the view that you're
  interacting with) or event (extra information about how the user is
  interacting with the view), do not include them in your arguments
- Which type to pick: be as specific as possible because using `AnyObject` can
  lead to crashes if you use methods and access properties that aren't actually
  available

Questions during the demo were:

> If you're writing an IBAction, for example, how do you know when self must be
> used to reference the local context?

Only when what the variable name refers to is ambiguous, which is rare in
practice (i.e. typically only in initializers of classes/structs/enums). Also,
this wasn't mentioned in the demo, but in closures, `self` is required.

> What's the difference between setting the sender as AnyObject vs UIButton?

If the sender is `AnyObject`, there are no checks on what the sender can and
can't actually handle. If I have an action from a `UIButton` but the sender is
`AnyObject`, the compiler won't complain if I do `sender.setOn(true, animated:
true)` but since that's a `UISwitch` method, when I click on the button in the
app, the app will crash.

> So can I have one action function respond to multiple UI Elements?

Yes! There's an example of this in the code.

> How did he pop up the help, and what help file is being displayed?

Chrisna uses a program called [Dash][dash] to bring up documentation. Dash is a
program that stores all sorts of documentation on different languages and
frameworks offline so you can access them at any time. Unfortunately, the free
version is pretty crippled, but he thinks that it's well worth its price. To
bring up Xcode's documentation, the shortcut Command-Shift-0 works. Chrisna has
Dash appear instead with that shortcut, which is what he uses throughout the
demo.

### Outlets

### Outlet Collections

Outlet collections are an array of outlets. You can use them if you want to do
similar things (in, say, a for loop) to a lot of the same type of outlet. The
example in the [code example][actions] Chrisna went through turns a few
switches on and off depending upon which button is pressed.

Note that even though an array implies order, the order of outlets in an outlet
collection is not guaranteed.

Questions during the demo were:

> I noticed that you used a for/in loop but can one use a switch statement in
> outlet collections in case one wants to switch switches on and off based on
> conditions?

Yes, one could use a switch statement, but since order of outlets inside an
outlet collection isn't guaranteed, that solution might not work. If the
conditions aren't based on which switch you want to modify, the switch
statement would be good.

> How do you add a view object into a collection? Should all objects in an
> outlet collection be the same type?

You can hold down Control and drag from the object over the collection and wait
until a blue rectangle appears above the outlet collection. All objects in an
outlet collection should be the same. This is enforced by Swift. For instance,
when I created an outlet collection of Switches, the array type was
`[UISwitch]`.

## Extra Questions

Gabrielle joined us for an extended question and answer period after the demo:

### INSERT QUESTION ABOUT IF/LET HERE

> Can you demonstrate how to unwind to a previous screen from a button on a
> second screen in swift or is it as simple as just dragging and connecting
> from the button on the second screen to the ViewController of the first
> screen?

I'm assuming here that, by unwinding, your scenes are inside a
`UINavigationController`.

You would create an action in your second scene's view controller from that
button. In that action, you would use the (optional) property
`navigationController`, which, according to the [documentation][vc], gives you
the "closest" navigation controller. Then, once you have access to the
navigation controller, you would call the `popViewControllerAnimated(_:)`
function, which is documented [here][nc].

> All are instance variables public? In Objective-C, public properties were
> declared in the .h file. How do public/private variables work in Swift?

In Swift, there's public access, internal access, and private access. Things
are internal access by default, which means that any source file in the module
(usually your app) can access it. Most developers recommend making everything
private unless it doesn't have to be, which means that access is restricted to
the file itself. Public means that other modules can import your code and use
your classes and functions and properties. More details can be found in Apple's
[Swift Programming Language][swift] book.

> In the color switcher, the View (the color block) was shown in the outline
> nested within another View item. I didn't see what made that happen and the
> one I added was at the same level as the other elements. Why the difference?
> Any significance?

No significance other than it was an easy way to put a border around the color
view.

> Are we going to cover any Apple Watch concepts in the course -- or a
> follow-up optional course/lesson? I'd love to do it as part of the final
> project.

Maybe in the future, but we have no concrete plans yet to cover it. You're more
than welcome to have an Apple Watch app be part of your final project, however!

> Will this course guide us on how to place our apps in the App Store and
> working with iTunes Connect?

The fifth course, which has not yet been released, will touch on that.

> How many students are in the March cohort?

Several hundred! This number will go up and down while free trials end, so
we'll have better numbers to report in a week or two.

### INSERT OTHER QUESTIONS AND ANSWERS HERE

> Is it safe to use a syntax like "for touch in event.allTouches()?.allObjects
> as? \[UITouch\] {..." rather than making the constant touches?

As of Xcode 6.2, you're not actually allowed to do this. This is because what
you have at the end is of type `[UITouch]?`, which is something that you can't
iterate through. What you can do is use the `??` operator, so you'd have
something like `for touch in event.allTouches()?.allObjects as? [UITouch] ??
[]`, but I prefer the `if`/`let` syntax.

> Could you provide instructions afterwards on getting and installing "Dash"
> into Xcode?

It's a separate app available on the Mac App Store. Here's their [site][dash].

> It may not be possible to do this for developers coming from other languages,
> but could you please make comparisons between Swift and Objective-C where you
> think this might be needed?

For this particular demo, there aren't that many differences. I've uploaded an
Objective-C version of the demo [here][actions-objc].

[hangout]: https://plus.google.com/u/0/events/c824hakd0ntm4maenep575897e8
[portal]: https://www.udacity.com/course/nd003
[actions]: https://github.com/ccrazy88/actions-and-outlets
[dash]: http://kapeli.com/dash
[swift]: https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/AccessControl.html
[vc]: https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIViewController_Class/#//apple_ref/occ/instp/UIViewController/navigationController
[nc]: https://developer.apple.com/library/ios/documentation/UIKit/Reference/UINavigationController_Class/
[actions-objc]: https://github.com/ccrazy88/actions-and-outlets-objc
