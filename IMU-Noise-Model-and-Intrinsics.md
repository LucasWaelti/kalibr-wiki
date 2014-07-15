The [Camera-IMU calibration](Camera-IMU-calibration) routine needs to know how "noisy" your IMU is. This is specified in your [IMU configuration YAML file](yaml-formats) before you start the calibration. This wiki page explains how to set these parameters and how to interpret them.

## The IMU Noise Model

The model used to describe IMU errors in Kalibr has two components:

1. Additive "white noise" that fluctuates rapidly
2. A slowly varying sensor "bias"



## How to Obtain the Parameters

### From the Datasheet of the IMU
### From the Allan Variance


<script type="text/x-mathjax-config">
MathJax.Hub.Register.StartupHook("HTML-CSS Jax Ready",function () {
  var HTMLCSS = MathJax.OutputJax["HTML-CSS"];
  HTMLCSS.Augment({
    OldPreTranslate: HTMLCSS.preTranslate,  // cache original preTranslate
    //
    //  Call original preTranslate (sets the HTMLCSS.display values used below)
    //  Then separate the scripts into inline and display ones
    //  Finally, make the scripts be inline followed by the display
    //
    preTranslate: function (state) {
      this.OldPreTranslate(state);
      var scripts = state.scripts, inline = [], display = [];
      for (var i = 0, m = scripts.length; i < m; i++) {
        (scripts[i].MathJax.elementJax.HTMLCSS.display ? display : inline).push(scripts[i]);
      }
      state.scripts = inline.concat(display);
    }
  })
});
MathJax.Hub.Register.MessageHook("New Math",function (message) {console.log(message[1])});
</script>
