<template>
  <div class="just-another-dropdown" >
    <div @click="toggle" class="select_label" :class="{'value-selected': value}">
      <span>{{value ? value : placeholder}}</span>
      <span class="arrow" :class="{'down-arrow': opened}">&#8250;</span>
    </div>
    <transition name="fade">
      <ul class="dropdown" v-if="opened">
        <li v-for="option in options"><a @click="change(option)" > {{option}}</a></li>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  data () {
    return {
      opened: false
    }
  },
  props: {
    value: {
      required: true
    },
    options: {
      type: Array,
      required: true
    },
    onChange: {
      type: Function,
      required: false
    },
    disabled: {
      type: Boolean
    },
    placeholder: {
      type: String
    },
    triggerToggle: {
      type: Boolean
    }
  },
  methods: {
    change (opt) {
      this.opened = false
      this.$emit('input', opt)

      if (this.onChange !== undefined) {
        this.onChange(this.value)
      }
    },
    toggle () {
      if (this.disabled) {
        return
      }
      this.opened = !this.opened
    }
  },
  watch: {
    triggerToggle: function () {
      this.toggle()
    }
  }
}
</script>

<style lang="css">
.just-another-dropdown {
    /* Size and position */
	position: relative;
	width: 100%;
	margin: 0 auto;
	padding: 10px;
    /* Styles */
	background: #fff;
	cursor: pointer;
	outline: none;
  border: solid 1.4px #ebebed;
  text-align: left;
    /* Font settings */
	font-weight: bold;
	color: #8AA8BD;
	text-transform: uppercase;
}

.just-another-dropdown .arrow{
  font-size: 2rem;
  height: 2.3rem;
}

.just-another-dropdown .arrow.down-arrow{
  transform: rotate(90deg);
  width: 2rem;
}

.just-another-dropdown .select_label.value-selected {
  font-size: 12.8px;
  line-height: 2rem;
  color: #212121;
}

.just-another-dropdown .select_label {
  height: 2rem;
  font-family: Montserrat;
  font-size: 12.8px;
  letter-spacing: 0.5px;
  color: #9b9b9b;
  display: flex;
  align-items: center;
}

/*.just-another-dropdown:after {
	content: "";
	width: 0;
	height: 0;
	position: absolute;
	right: 15px;
	top: 50%;
	margin-top: -3px;
	border-width: 6px 6px 0 6px;
	border-style: solid;
	border-color: #8aa8bd transparent;
}*/



.just-another-dropdown i{
  padding-left: 1rem;
}
.just-another-dropdown span {
  padding-left: 1.3rem;
}

.just-another-dropdown .dropdown {
  /* Size & position */
	position: absolute;
	top: 115%;
	left: 0;
	right: 0;
  padding-left: 10px;
    /* Styles */
	background: white;
	border-radius: inherit;
	border: 1px solid rgba(0,0,0,0.17);
	box-shadow: 0 0 5px rgba(0,0,0,0.1);
	font-weight: normal;
	transition: all 0.5s cubic-bezier(0.07, 0.68, 0.56, 0.62);
	list-style: none;

  pointer-events: auto;
}

.just-another-dropdown .dropdown li a {
	display: block;
	padding: 10px;
	text-decoration: none;
  color: #212121;
  font-family: Montserrat;
  letter-spacing: 0.5px;
  font-size: 12.8px;
	border-bottom: 1px solid #e6e8ea;
	box-shadow: inset 0 1px 0 rgba(255,255,255,1);
	/*transition: all 0.3s ease-out;*/
}

.just-another-dropdown .dropdown li:first-of-type a {
	border-radius: 7px 7px 0 0;
}

.just-another-dropdown .dropdown li:last-of-type a {
	border-radius: 0 0 7px 7px;
	border: none;
}

/* Hover state */

.just-another-dropdown .dropdown li:hover a {
	background: #d4effc;
}

.just-another-dropdown .dropdown:after {
	content: "";
	width: 0;
	height: 0;
	position: absolute;
	bottom: 100%;
	right: 15px;
	border-width: 0 6px 6px 6px;
	border-style: solid;
	border-color: #fff transparent;
}

.just-another-dropdown .dropdown:before {
	content: "";
	width: 0;
	height: 0;
	position: absolute;
	bottom: 100%;
	right: 13px;
	border-width: 0 8px 8px 8px;
	border-style: solid;
	border-color: rgba(0,0,0,0.1) transparent;
}
/*
.just-another-dropdown.active .dropdown {
	opacity: 1;
	pointer-events: auto;
  z-index: 999 !important;
}*/
</style>
