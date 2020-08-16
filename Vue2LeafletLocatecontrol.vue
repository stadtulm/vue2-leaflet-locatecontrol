<script>
import { DomEvent } from 'leaflet';
import { OptionsMixin, ControlMixin, propsBinder, optionsMerger, findRealParent } from 'vue2-leaflet';
import LocateControl from "leaflet.locatecontrol";
import 'leaflet.locatecontrol/dist/L.Control.Locate.css';

const props = {
  position: {
    type: String,
    default: 'topleft'
  }
}

export default {
  name: "LLocateControl",

  mixins: [ControlMixin, OptionsMixin],

  props: props,

  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);
    this.mapObject = new LocateControl(options);
    DomEvent.on(this.mapObject, this.$listeners);
    propsBinder(this, this.mapObject, this.$options.props);
    this.parentContainer = findRealParent(this.$parent);
    this.mapObject.addTo(this.parentContainer.mapObject);
  },

  render () {
    return null;
  }
}
</script>