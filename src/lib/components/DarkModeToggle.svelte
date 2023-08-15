<script>
  export let lightModeColor = '#000000'
  export let lightModeHover = '#292828'
  export let darkModeColor = '#FFFFFF'
  export let darkModeHover = '#e6e6e6'
  export let animationDuration = '.25s'
  export let animationDelay = '.25s'
  export let size = '28px'
  export let title = 'Toggle dark mode'
  export let darkMode
</script>

<button class="theme-toggle"
        {title}
        style='--hoverColor: {darkMode ? darkModeHover : lightModeHover};
          --animationDuration: {animationDuration};
          --animationDelay: {animationDelay}'
        class:dark-mode={darkMode}
        on:click>
  <svg class="sun-and-moon" aria-hidden="true" width={size} height={size} viewBox="0 0 24 24">
    <mask class="moon" id="moon-mask">
      <rect x="0" y="0" width="100%" height="100%" fill="white"/>
      <circle cx="24" cy="10" r="6" fill='black'/>
    </mask>

    <circle class="sun" cx="12" cy="12" r="5" mask="url(#moon-mask)" fill={darkMode ? darkModeColor : lightModeColor} />

    <g class="sun-beams" stroke={lightModeColor} stroke-width="2px">
      <line x1="12" y1="1" x2="12" y2="4" />
      <line x1="17.6568" y1="6.3431" x2="19.7781" y2="4.2218" />
      <line x1="20" y1="12" x2="23" y2="12" />
      <line x1="17.6568" y1="17.6568" x2="19.7781" y2="19.7781" />
      <line x1="12" y1="20" x2="12" y2="23" />
      <line x1="6.3431" y1="17.6568" x2="4.2218" y2="19.7781" />
      <line x1="1" y1="12" x2="4" y2="12" />
      <line x1="6.3431" y1="6.3431" x2="4.2218" y2="4.2218" />
    </g>
  </svg>
</button>

<style>
  .theme-toggle {
    border: 0;
    background-color: transparent;
  }
  .sun-and-moon > :is(.moon, .sun, .sun-beams) {
    transform-origin: center;
  }

  .theme-toggle:is(:hover, :focus-visible) > .sun-and-moon > :is(.moon, .sun) {
    fill: var(--hoverColor);
  }

  .theme-toggle:is(:hover, :focus-visible) .sun-and-moon > .sun-beams {
    stroke: var(--hoverColor);
  }

  .sun{
    transition: transform calc(var(--animationDuration) * 2) cubic-bezier(.5,1.25,.75,1.25);
  }

  .dark-mode .sun {
    transition-timing-function: cubic-bezier(.25,0,.3,1);
    transition-duration: var(--animationDuration);
    transform: scale(1.75);
  }

  .sun-beams {
    stroke-linecap: round;
    transition: transform .5s ease, opacity .5s cubic-bezier(.5,1.5,.75,1.25);
  }

  .dark-mode .sun-beams {
    transition-duration: var(--animationDuration);
    transform: rotateZ(-25deg);
    opacity: 0;
  }

  .moon > circle {
    transition: transform var(--animationDuration) cubic-bezier(0,0,0,1);
  }

  .dark-mode .moon > circle {
    transition: transform var(--animationDuration) cubic-bezier(0,0,0,1);
    transition-delay: var(--animationDelay);
    transform: translateX(-7px);
  }
</style>