<template>
  <div>
    <div class="layout-padding" style="padding-bottom: 1000px;">
      <p class="caption">
        <span class="desktop-only">
          Right click anywhere on the Page below (not on header though).
          <br>
          On a real mobile device it works different by opening a minimized Modal triggered by a long tap.
        </span>
        <span class="mobile-only">
          Long Tap anywhere on the Page below (not on header though).
          <br>
          On a desktop it works different by opening a Popover.
        </span>
      </p>
      <blockquote>
        <small>
          Works with any elements you want. It doesn't have to be a List.
        </small>
      </blockquote>
      <p class="caption">
        <span class="mobile-only">
          On a desktop browser user
        </span>
        <span class="desktop-only">
          User
        </span>
        can dismiss the Context Menu
        by hitting the &lt;ESCAPE&gt; key.
      </p>
    </div>

    <q-context-menu ref="context">
      <q-list link delimiter style="min-width: 150px; max-height: 300px;">
        <q-item
          v-for="n in 10"
          :key="n"
          @click="showToast(), $refs.context.close()"
        >
          <q-item-main label="Label" sublabel="Value" />
        </q-item>
      </q-list>
    </q-context-menu>
  </div>
</template>

<script>
import { Platform, Toast } from 'quasar'

export default {
  methods: {
    showToast () {
      Toast.create((Platform.is.desktop ? 'Clicked' : 'Tapped') + ' on a context menu item.')
    }
  }
}
</script>
