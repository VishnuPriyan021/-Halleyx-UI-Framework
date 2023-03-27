<template>
  <h1 class="component-heading">Color picker</h1>
  <p class="component-description">
    <!-- Write your component description here -->
This component allows for a fully accessible and configurable color picker, allowing the user to pick from a set of predefined colors (swatches).
  </p>
  <divider :position="'horizontal'" :space="'20px'" />
  <!-- <h2 class="component-side-heading">Sub-heading area</h2> -->
  <!-- <p class="component-description">Choose the color and get value of the color</p> -->
  <div class="notes">
    <!-- <p class="note-title" >Note:</p><p class="note-body">Add notes here with <i></i> tags to highlight words in italic  </p> -->
  </div>
  <div class="component-example">
    <div class="example-body">
      <!-- <color-picker/> -->
      <div class="color-space">

      </div>
      <div class="color-picker-panel">
        <div class="panel-row">
          <div class="swatches default-swatches"></div>
          <button class="button eyedropper">Get Color</button>
        </div>
        <div class="panel-row">
          <div class="spectrum-map">
            <button id="spectrum-cursor" class="color-cursor"></button>
            <canvas id="spectrum-canvas"></canvas>
          </div>
          <div class="hue-map">
            <button id="hue-cursor" class="color-cursor"></button>
            <canvas id="hue-canvas"></canvas>
          </div>
        </div>
        <div class="panel-row">
          <div id="rgb-fields" class="field-group value-fields rgb-fields active">
            <div class="field-group">
              <label for="" class="field-label">R:</label>
              <input type="number" max="255" min="0" id="red" class="field-input rgb-input">
            </div>
            <div class="field-group">
              <label for="" class="field-label">G:</label>
              <input type="number" max="255" min="0" id="green" class="field-input rgb-input">
            </div>
            <div class="field-group">
              <label for="" class="field-label">B:</label>
              <input type="number" max="255" min="0" id="blue" class="field-input rgb-input">
            </div>
          </div>
          <div id="hex-field" class="field-group value-fields hex-field">
            <label for="" class="field-label">Hex:</label>
            <input type="text" id="hex" class="field-input">
          </div>
          <button id="mode-toggle" class="button mode-toggle">Mode</button>
        </div>
        <div class="panel-row">
          <h2 class="panel-header">User Colors</h2>
          <div id="user-swatches" class="swatches custom-swatches"></div>
          <button id="add-swatch" class="button add-swatch">
            <span id="color-indicator" class="color-indicator"></span>
            <span>Add to Swatches</span>
          </button>
        </div>
      </div>
    </div>
    <div class="example-footer">
        <!-- Replace your id wherever required -->
      <span class="icon" id="color-picker-icon" @click="showCode('color-picker')"><i class="icon-code-regular"></i></span>
    </div>
  </div>
  <div class="source-code" id="color-picker" style="display: none">
    <section class="example-source-wrapper">
        <div class="source">
          <CodeEditor
             :id="'editor'"  :display_language="false"
            :value="color_picker"
            :read_only="true"
            :theme="editor_theme"
            :languages="[
              ['Javascript', 'Vue'],
              ['javascript', 'JS'],
              ['python', 'Python'],
            ]"
          />
        </div>
      </section>
  </div>
  <divider :position="'horizontal'" :space="'20px'" />
</template>

<script>
import CodeEditor from 'simple-code-editor'
// import ColorPicker from '../components/ColorPicker.vue'
import tinycolor from 'tinycolor2'
export default {
  components: {
    CodeEditor,
    ColorPicker
  },
  data () {
    return {
      editor_theme: 'light',
      color_picker: `<template>
        <color-picker/>
      </template>`
    }
  },
  mounted(){
    this.call()
  },
  methods: {
    showCode (val) {
      document.getElementById(val + '-icon').classList.toggle('active-icon')
      if (document.getElementById(val).style.display === 'none') {
        document.getElementById(val).style.display = 'block'
      } else if (document.getElementById(val).style.display === 'block') {
        document.getElementById(val).style.display = 'none'
      }
    },
    call(){
            var addSwatch = document.getElementById('add-swatch');
      var modeToggle = document.getElementById('mode-toggle');
      var swatches = document.getElementsByClassName('default-swatches')[0];
      var colorIndicator = document.getElementById('color-indicator');
      var userSwatches = document.getElementById('user-swatches');

      var spectrumCanvas = document.getElementById('spectrum-canvas');
      var spectrumCtx = spectrumCanvas.getContext('2d');
      var spectrumCursor = document.getElementById('spectrum-cursor');
      var spectrumRect = spectrumCanvas.getBoundingClientRect();

      var hueCanvas = document.getElementById('hue-canvas');
      var hueCtx = hueCanvas.getContext('2d');
      var hueCursor = document.getElementById('hue-cursor');
      var hueRect = hueCanvas.getBoundingClientRect();

      var currentColor = '';
      var hue = 0;
      var saturation = 1;
      var lightness = .5;

      var rgbFields = document.getElementById('rgb-fields');
      var hexField = document.getElementById('hex-field');

      var red = document.getElementById('red');
      var blue = document.getElementById('blue');
      var green = document.getElementById('green');
      var hex = document.getElementById('hex');

      function ColorPicker() {
        this.addDefaultSwatches();
        createShadeSpectrum();
        createHueSpectrum();
      };

      ColorPicker.prototype.defaultSwatches = [
        '#FFFFFF',
        '#FFFB0D',
        '#0532FF',
        '#FF9300', 
        '#00F91A', 
        '#FF2700', 
        '#000000', 
        '#686868', 
        '#EE5464', 
        '#D27AEE', 
        '#5BA8C4', 
        '#E64AA9'
      ];

      function createSwatch(target, color) {
        var swatch = document.createElement('button');
        swatch.classList.add('swatch');
        swatch.setAttribute('title', color);
        swatch.style.backgroundColor = color;
        swatch.addEventListener('click', function(){
          var color = tinycolor(this.style.backgroundColor);
          colorToPos(color);
          setColorValues(color);
        });
        target.appendChild(swatch);
        refreshElementRects();
      };

      ColorPicker.prototype.addDefaultSwatches = function() {
        for( var i = 0; i < this.defaultSwatches.length; ++i) {
          createSwatch(swatches, this.defaultSwatches[i]);
        }
      }

      function refreshElementRects() {
        spectrumRect = spectrumCanvas.getBoundingClientRect();
        hueRect = hueCanvas.getBoundingClientRect();
      }

      function createShadeSpectrum(color) {
        let canvas = spectrumCanvas;
        let ctx = spectrumCtx;
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        if(!color) color = '#f00';
        ctx.fillStyle = color;
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        var whiteGradient = ctx.createLinearGradient(0, 0, canvas.width, 0);
        whiteGradient.addColorStop(0, "#fff");
        whiteGradient.addColorStop(1, "transparent");
        ctx.fillStyle = whiteGradient;
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        var blackGradient = ctx.createLinearGradient(0, 0, 0, canvas.height);
        blackGradient.addColorStop(0, "transparent");
        blackGradient.addColorStop(1, "#000");
        ctx.fillStyle = blackGradient;
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        canvas.addEventListener('mousedown', function(e) {
          startGetSpectrumColor(e);
        });
      };

      function createHueSpectrum() {
        var canvas = hueCanvas;
        var ctx = hueCtx;
        var hueGradient = ctx.createLinearGradient(0, 0, 0, canvas.height);
        hueGradient.addColorStop(0.00, "hsl(0, 100%, 50%)");
        hueGradient.addColorStop(0.17, "hsl(298.8, 100%, 50%)");
        hueGradient.addColorStop(0.33, "hsl(241.2, 100%, 50%)");
        hueGradient.addColorStop(0.50, "hsl(180, 100%, 50%)");
        hueGradient.addColorStop(0.67, "hsl(118.8, 100%, 50%)");
        hueGradient.addColorStop(0.83, "hsl(61.2, 100%, 50%)");
        hueGradient.addColorStop(1.00, "hsl(360, 100%, 50%)");
        ctx.fillStyle = hueGradient;
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        canvas.addEventListener('mousedown', function(e) {
          startGetHueColor(e);
        });
      };

      function colorToHue(color) {
        var color = tinycolor(color);
        var hueString = tinycolor('hsl ' + color.toHsl().h + ' 1 .5').toHslString();
        return hueString;
      };

      function colorToPos(color) {
        var color = tinycolor(color);
        var hsl = color.toHsl();
        hue = hsl.h;
        var hsv = color.toHsv();
        var x = spectrumRect.width * hsv.s;
        var y = spectrumRect.height * (1 - hsv.v);
        var hueY = hueRect.height - ((hue / 360) * hueRect.height);
        updateSpectrumCursor(x, y);
        updateHueCursor(hueY);
        setCurrentColor(color);
        createShadeSpectrum(colorToHue(color));
      };

      function setColorValues(color) {
        var color = tinycolor(color);
        var rgbValues = color.toRgb();
        var hexValue = color.toHex();
        
        red.value = rgbValues.r;
        green.value = rgbValues.g;
        blue.value = rgbValues.b;
        hex.value = hexValue;
      };

      function setCurrentColor(color) {
        color = tinycolor(color);
        currentColor = color;
        colorIndicator.style.backgroundColor = color;
        var body =document.querySelector('.color-space')
        body.style.backgroundColor = color;
        spectrumCursor.style.backgroundColor = color;
        hueCursor.style.backgroundColor = 'hsl(' + color.toHsl().h +',100%, 50%)';
      };

      function updateHueCursor(y) {
        hueCursor.style.top = y + "px";
      }

      function updateSpectrumCursor(x, y) {
        spectrumCursor.style.left = x + 'px';
        spectrumCursor.style.top = y + 'px';
      };

      var startGetSpectrumColor = function(e) {
        getSpectrumColor(e);
        spectrumCursor.classList.add('dragging');
        window.addEventListener('mousemove', getSpectrumColor);
        window.addEventListener('mouseup', endGetSpectrumColor);
      };

      function getSpectrumColor(e) {
        e.preventDefault();
        
        var x = e.pageX - spectrumRect.left;
        var y = e.pageY - spectrumRect.top;
        
        if(x > spectrumRect.width) {x = spectrumRect.width}
        if(x < 0) {x = 0}
        if(y > spectrumRect.height) {y = spectrumRect.height}
        if(y < 0) {y = .1}
        
        var xRatio = x / spectrumRect.width * 100;
        var yRatio = y / spectrumRect.height * 100;
        var hsvValue = 1 - (yRatio / 100);
        var hsvSaturation = xRatio / 100;
        lightness = (hsvValue / 2) * (2 - hsvSaturation);
        saturation = (hsvValue * hsvSaturation) / (1 - Math.abs(2 * lightness -1));
        var color = tinycolor('hsl ' + hue + ' ' + saturation + ' ' + lightness);
        setCurrentColor(color);
        setColorValues(color);
        updateSpectrumCursor(x, y);
      };

      function endGetSpectrumColor(e) {
        spectrumCursor.classList.remove('dragging');
        window.removeEventListener('mousemove', getSpectrumColor);
      };

      function startGetHueColor(e) {
        getHueColor(e);
        hueCursor.classList.add('dragging');
        window.addEventListener('mousemove', getHueColor);
        window.addEventListener('mouseup', endGetHueColor);
      }

      function getHueColor(e) {
        e.preventDefault();
        var y = e.pageY - hueRect.top;
        if (y > hueRect.height){ y = hueRect.height};
        if (y < 0) { y = 0};
        var percent = y / hueRect.height;
        hue = 360 - (360 * percent);
        var hueColor = tinycolor('hsl ' + hue + ' 1 .5').toHslString();
        var color = tinycolor('hsl ' + hue + ' ' + saturation + ' ' + lightness).toHslString();
        createShadeSpectrum(hueColor);
        updateHueCursor(y, hueColor);
        setCurrentColor(color);
        setColorValues(color);
      };

      function endGetHueColor(e) {
        hueCursor.classList.remove('dragging');
        window.removeEventListener('mousemove', getHueColor);
      };

      red.addEventListener('change', function() {
        var color = tinycolor('rgb ' + red.value + ' ' + green.value + ' ' + blue.value);
        colorToPos(color);
      });

      green.addEventListener('change', function() {
        var color = tinycolor('rgb ' + red.value + ' ' + green.value + ' ' + blue.value);
        colorToPos(color);
      });

      blue.addEventListener('change', function() {
        var color = tinycolor('rgb ' + red.value + ' ' + green.value + ' ' + blue.value);
        colorToPos(color);
      });

      addSwatch.addEventListener('click', function() {
        createSwatch(userSwatches , currentColor);
      });

      modeToggle.addEventListener('click', function() {
        if(rgbFields.classList.contains('active') ? rgbFields.classList.remove('active') : rgbFields.classList.add('active'));
        if(hexField.classList.contains('active') ? hexField.classList.remove('active') : hexField.classList.add('active'));
      });

      window.addEventListener('resize', function() {
        refreshElementRects();
      });

      new ColorPicker();
          }

  }
}
</script>

<style lang="scss" scoped>
.color-space{
  width: 60px;
  height: 40px;
}
.color-picker-panel {
  background: #1f232a;
  width: 310px;
  border-radius: 8px;
  border: 2px solid #364347;
  box-shadow: 0 4px 12px rgba(0, 0, 0, .4);
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.panel-row {
  position: relative;
  margin: 0 10px 10px;
}
.panel-row:first-child {
  margin-top: 10px;
  margin-bottom: 6px;
}
.panel-row:after {
  content: '';
  display: table;
  clear: both;
}
.panel-header {
  background: #15191c;
  padding: 8px;
  margin: 0 -10px 10px;
  text-align: center;
}
.swatch {
  display: inline-block;
  width: 32px;
  height: 32px;
  background: #ccc;
  border-radius: 4px;
  margin-left: 4px;
  margin-bottom: 4px;
  box-sizing: border-box;
  border: 2px solid #364347;
  cursor: pointer;
}
.default-swatches {
  width: 212px;
}
.default-swatches .swatch:nth-child(6n + 1) {
  margin-left: 0;
}
.color-cursor {
  border-radius: 100%;
  background: #ccc;
  box-sizing: border-box;
  position: absolute;
  pointer-events: none;
  z-index: 2;
  border: 2px solid #fff;
  transition: all 0.2s ease;
}
.color-cursor.dragging {
  transition: none;
}
.color-cursor#spectrum-cursor {
  width: 30px;
  height: 30px;
  margin-left:- 15px;
  margin-top: - 15px;
  top: 0;
  left: 0;
}
.color-cursor#hue-cursor {
  top: 0;
  left: 50%;
  height: 20px;
  width: 20px;
  margin-top: -10px;
  margin-left: -10px;
  pointer-events: none;
}
.spectrum-map {
  position: relative;
  width: 212px;
  height: 200px;
  overflow: hidden;
}
#spectrum-canvas {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: #ccc;
}
.hue-map {
  position: absolute;
  top: 5px;
  bottom: 5px;
  right: 29px;
  width: 10px;
}
#hue-canvas {
  border-radius: 8px;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  background: #ccc;
}
.button {
  background: #2a3137;
  border: 0;
  border-radius: 4px;
  color: #8b949a;
  font-size: 1rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .2);
  outline: none;
  cursor: pointer;
  padding: 4px;
}
button:active {
  background: #262c31;
}
.button.eyedropper {
  position: absolute;
  right: 0;
  top: 0;
  width: 68px;
  height: 68px;
  display: block;
}
.button.add-swatch {
  display: block;
  padding: 6px;
  width: 200px;
  margin: 10px auto 0;
}
.button.mode-toggle {
  position: absolute;
  top: 0;
  right: 0;
  width: 68px;
  height: 40px;
  margin: 0;
}
.value-fields {
  display: none;
  align-items: center;
}
.value-fields.active {
  display: flex;
}
.value-fields .field-label {
  margin-right: 6px;
}
.value-fields .field-input {
  background: #15191c;
  border: 1px solid #364347;
  box-sizing: border-box;
  border-radius: 2px;
  line-height: 38px;
  padding: 0 4px;
  text-align: center;
  color: #8b949a;
  font-size: 1rem;
  display: block;
}
.rgb-fields .field-group {
  display: flex;
  align-items: center;
}
.rgb-fields .field-input {
  width: 42px;
  margin-right: 10px;
}
.hex-field .field-input {
  width: 170px;
}
.color-indicator {
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 20px;
  height: 20px;
  border-radius: 4px;
  background: #ccc;
}
input::-webkit-outer-spin-button, input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
