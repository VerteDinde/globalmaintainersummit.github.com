<template>
  <div class="schedule">
    <ScheduleDay
      v-for="day in schedule"
      :key="day.slug"
      :content="day"
      class="day"
    />
  </div>
</template>

<script>
import socialMetadata from '~/mixins/social-metadata'

export default {
  mixins: [socialMetadata],
  async asyncData({ $content }) {
    const schedule = await $content('2021/pages/schedule')
      .sortBy('slug')
      .fetch()

    return {
      schedule,
    }
  },
}
</script>

<style lang="scss" scoped>
.schedule {
  @include section();
}

.day {
  margin: 40px;
  &:last-child {
    margin-top: 120px;
  }
}
</style>
