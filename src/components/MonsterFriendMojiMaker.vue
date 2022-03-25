<template>
  <h1>mfmoji maker</h1>
  <div class="mfmoji-maker">
    <div>
      <h3>Foreground Emoji</h3>
      <button :class="foregroundEmoji == '⬛️' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '⬛️'">⬛️</button>
      <button :class="foregroundEmoji == '⬜️' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '⬜️'">⬜️</button>
      <button :class="foregroundEmoji == '🟫' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟫'">🟫</button>
      <button :class="foregroundEmoji == '🟩' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟩'">🟩</button>
      <button :class="foregroundEmoji == '🟥' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟥'">🟥</button>
      <button :class="foregroundEmoji == '🟦' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟦'">🟦</button>
      <button :class="foregroundEmoji == '🟧' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟧'">🟧</button>
      <button :class="foregroundEmoji == '🟪' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟪'">🟪</button>
      <button :class="foregroundEmoji == '🟨' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟨'">🟨</button>
      <button :class="foregroundEmoji == '🟢' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟢'">🟢</button>
      <button :class="foregroundEmoji == '🟠' ? activeStyle : inactiveStyle" v-on:click="foregroundEmoji = '🟠'">🟠</button>
    </div>

    <div>
      <h3>Background Emoji</h3>
      <button :class="backgroundEmoji == '⬛️' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '⬛️'">⬛️</button>
      <button :class="backgroundEmoji == '⬜️' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '⬜️'">⬜️</button>
      <button :class="backgroundEmoji == '🟫' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟫'">🟫</button>
      <button :class="backgroundEmoji == '🟩' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟩'">🟩</button>
      <button :class="backgroundEmoji == '🟥' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟥'">🟥</button>
      <button :class="backgroundEmoji == '🟦' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟦'">🟦</button>
      <button :class="backgroundEmoji == '🟧' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟧'">🟧</button>
      <button :class="backgroundEmoji == '🟪' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟪'">🟪</button>
      <button :class="backgroundEmoji == '🟨' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟨'">🟨</button>
      <button :class="backgroundEmoji == '🟢' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟢'">🟢</button>
      <button :class="backgroundEmoji == '🟠' ? activeStyle : inactiveStyle" v-on:click="backgroundEmoji = '🟠'">🟠</button>
    </div>

    <div>
      <h3>Your masterpiece</h3>
      <button v-on:click="copy(backgroundEmoji, foregroundEmoji)">Copy to clipboard</button>
      <span class="pre-wrap">{{mfparty}}</span>
    </div>
  </div>
  <p>Made with ❤️ by erran. Inspired by a <a href="https://twitter.com/mintrainmint/status/1507086119703355402?s=20&t=4Po1jh6vasgpwgN45kDBLg">cool Tweet by @mintrain</a>.</p>
</template>

<style scoped>
h3 {
  font-size: 1.2rem;
}

#mfmoji-maker {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 0 2rem;
}

.active-emoji {
  border: red;
  border-style: groove;
}

.inactive-emoji {
  border: blue;
  border-style: groove;
}

.pre-wrap {
  display: block;
  white-space: pre-wrap;
}
</style>

<script lang="ts">
import { defineComponent } from 'vue';

const activeStyle = 'active-emoji';
const inactiveStyle = 'inactive-emoji';
// The OG by mintrain:
const mfmoji = `🟪🟪🟪🟨🟨🟪🟪🟪
🟪🟪🟨🟨🟨🟨🟪🟪
🟪🟨🟨🟪🟨🟪🟨🟪
🟨🟨🟨🟨🟨🟨🟨🟨
🟨🟪🟨🟨🟨🟨🟪🟨
🟨🟪🟨🟨🟨🟨🟪🟨
🟪🟪🟨🟪🟪🟨🟪🟪
🟪🟪🟨🟪🟪🟨🟪🟪
`;

export default defineComponent({
  data() {
    return {
      backgroundEmoji: '⬛️',
      foregroundEmoji: '⬜️',
    };
  },

  computed: {
    mfparty(ctx) {
      return mfmoji.replace(/🟪/g, ctx.backgroundEmoji)
        .replace(/🟨/g, ctx.foregroundEmoji);
    },
  },

  methods: {
    copy(backgroundEmoji: string, foregroundEmoji: string) {
      window.navigator.clipboard.writeText(mfmoji.replace(/🟪/g, backgroundEmoji)
        .replace(/🟨/g, foregroundEmoji));
    },
  },

  setup() {
    return {
      activeStyle,
      inactiveStyle,
    };
  },
});
</script>
