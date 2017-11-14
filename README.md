# ipfx.org-java
Java library which helps to work with (www.ipfx.org) animation interpolators. Feel free to contribute!

# Basic usage

1. go to (http://ipfx.org/)
2. create interpolator function
3. copy generated url (data is encoded in the url)
4. pass url as a parameter to Interpolator.parseUrl() method

## Super simple

```
import org.ipfx.Interpolator;
...
final Interpolator interpolator = Interpolator.parseUrl(urlData);
...
float y = interpolator.calc(x);
...
```

## Java Android example

```
final Interpolator interpolator = Interpolator.parseUrl(urlData);

ObjectAnimator animator = ObjectAnimator.ofFloat(testButton, View.Y, startY, endY);
animator.setDuration(1000);

animator.setInterpolator(new TimeInterpolator() {
    @Override
    public float getInterpolation(float input) {
        return interpolator.calc(input);
    }
});
animator.start();
```
