# Basic Layouts in Compose Codelab

This folder contains the source code for
the [Basic Layouts in Compose Codelab](https://developer.android.com/codelabs/jetpack-compose-layouts)

## License

```
No license. I am the owner now.
```

## Image asset attributions

[fc1_short_mantras.jpg](https://www.pexels.com/photo/body-of-water-view-1825206/) - Elizaveta Kozorezova

[fc2_nature_meditations.jpg](https://www.pexels.com/photo/photo-of-green-leaves-3571551/) - Nothing Ahead

[fc3_stress_and_anxiety.jpg](https://www.pexels.com/photo/aerial-view-of-body-of-water-1557238/) - Jim

[fc4_self_massage.jpg](https://www.pexels.com/photo/photography-of-stones-1029604/) - Scott Webb

[fc5_overwhelmed.jpg](https://www.pexels.com/photo/white-clouds-3560044/) - Ruvim

[fc6_nightly_wind_down.jpg](https://www.pexels.com/photo/time-lapse-photo-of-stars-on-night-924824/) - Jakub Novacek

[ab1_inversions.jpg](https://www.pexels.com/photo/low-angle-view-of-woman-relaxing-on-beach-against-blue-sky-317157/) - Chevanon Photography

[ab2_quick_yoga.jpg](https://www.pexels.com/photo/photo-of-woman-stretching-her-body-1812964/) - Agung Pandit Wiguna

[ab3_stretching.jpg](https://www.pexels.com/photo/photo-of-women-stretching-together-4056723/) - Cliff Booth

[ab4_tabata.jpg](https://www.pexels.com/photo/fashion-man-people-art-4662438/) - Elly Fairytale

[ab5_hiit.jpg](https://www.pexels.com/photo/man-wearing-white-pants-under-blue-sky-999309/) - The Lazy Artist Gallery

[ab6_pre_natal_yoga.jpg](https://www.pexels.com/photo/woman-doing-yoga-396133/) - freestocks.org

## Conclusions

1. Tutorial is very good, it gives the real world example how to implement user interface given a design.
2. Jetpack Compose is a little bit less bloated than Flutter. In Flutter, one must use spesific object to another object with often times little to no compromise. While this could mean that everyone's code is less fragmented, it could also possibly limit one's freedom of choice/creativity. But still, Compose's syntax is still ugly.
3. Implementing a user interface must be done with a strong "break to smaller pieces and find for reusability" sense in mind. In this example, notice that ```Align your Body``` and ```Favorite Collections``` both have different content body, but share a similar "headline with a body" structure. Hence, the implementation of ```@Composable fun HomeSection(modifier: Modifier = Modifier, @StringRes title: Int, content: @Composable () -> Unit)``` in the code. Using that composable function, we could implement both ```Align your Body``` and ```Favorite Collections``` by using a shared structure of ```HomeSection``` composable function aforementioned. Still, Compose's syntax is ugly.
4. Another "reusability" mind, notice that almost all of the composable functions within accepts a ```modifier``` parameter. That is so that we could pass global modification just in case. But in this case, we don't see it because the user interface is not complex enough.
5. Here we learned that we could use our lovely resources by using their id and pass them to ```painterResource()``` function for R.drawable.XXX and ```stringResource()``` for R.string.XXX. Ah, good ol'lovely Android MDC.
6. In portrait screen, we use ```Scaffold``` to structure our user interface bundled with screen's background color. In landscape screen however, since we want to move ```BottomNavigationBar``` to the left side of the screen (so that it follows Material 3 guidelines), we must use ```Row``` instead of relying to ```Scaffold```. There, we must also define the screen's background color for the ```Surface```'s ```color``` parameter because there is no ```Scaffold``` present to set that up for us automatically.
7. We could detect current screen's width by using ```val windowSizeClass = calculateWindowSizeClass(this)```'s ```widthSizeClass``` property. Then, we could match that ```widthSizeClass``` property to one of three possibilities either: ```Compact```, ```Medium```, or ```Expanded```. Hence the to do: implement the ```Expanded``` version of the screen for self challenge purpose. See the [screen width guideline](https://developer.android.com/static/codelabs/jetpack-compose-layouts/img/346355a616f580a5_1440.png) for better insight. HOWEVER, in the writing of this code that spesific library is still in experimental phase. And to make matter worse, running the original code from the tutorial (see link at the top of this document above) won't give the desired result for landscape screen in my phone A.K.A. turning my real phone to landscape mode would make the screen all white with nothing to see and interact with. Hence, in my implementation here I am using a hacky method by passing a new ```isLandscape``` variable and then compare that in the ```MySootheApp``` composable function hence the ```else if (windowSizeClass.widthSizeClass == WindowWidthSizeClass.Expanded || isLandscape)``` came from.

COMPOSE'S SYNTAX IS FUCKING UGLY AND I LOVE IT!!! Ugly means less magical things to deal with, and less magical is better for the developer.
