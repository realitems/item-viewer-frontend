<template>
  <div class="max-width mx-auto">
    <v-text-field
      v-model="itemId"
      color="grey"
      label="ITEM ID"
      placeholder="Enter item ID"
      hint="Example: 48094d2d-0cfd-47f5-b7f2-b24b570fb15f"
      persistent-hint
      persistent-placeholder
      outlined
      clearable
      autofocus
    />

    <v-btn
      class="mx-auto mt-4"
      color="primary"
      :to="`/${itemId}`"
      :disabled="!validItemId"
      nuxt
      block
      outlined
      :loading="loading"
      @click="loading = true"
    >
      View Item
    </v-btn>
  </div>
</template>

<script>
export default {
  data: () => ({
    itemId: undefined,
    loading: false,
  }),

  // Compute if itemId is in uuid v4 format
  computed: {
    validItemId() {
      const uuidV4Regex = new RegExp(
        "^[0-9a-f]{8}-[0-9a-f]{4}-4[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$",
        "i"
      );

      return uuidV4Regex.test(this.itemId);
    },
  },

  created() {},

  methods: {},
};
</script>

<!-- Setting lang="SCCSS" fixes reload issue -->
<!-- https://github.com/nuxt/nuxt/issues/5550 -->
<style lang="SCSS" scoped>
.max-width {
  width: 100%;
  max-width: 500px;
}
</style>
