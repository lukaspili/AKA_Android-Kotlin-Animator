# AKA - Android Kotlin Animator

Simple and convenient Kotlin DSL to work with Android animation API.


## Usage

```kotlin

// define an animation block that will start immediately
animate {
    interpolator = AccelerateDecelerateInterpolator()
    duration = 300

    // both animations run in parallel
    play(myView.animatedAlpha(0f))
    play(myOtherView.animatableTranslationY(100f))

    // this animation block will start when parent animation completes
    then {
    	// overrides the duration that was set in the parent animation block
    	duration = 500

    	// when the interpolator is not explicitly set, the animation block will get the interpolator from the parent animation block

        play(myNewView.animatedAlpha(1f))
    }

    onStart {
    	// before my animation start
    }

    onEnd {
     	// when the animation did end
    }
}
```