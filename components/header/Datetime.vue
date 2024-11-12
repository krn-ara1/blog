<script>
export default {
  data() {
    return {
      dayOfWeekList: ["Sun", "Mon", "Tues", "Wednes", "Thurs", "Fri", "Satur"],
      monthEnList: [
        "Jan.",
        "Feb.",
        "Mar.",
        "Apr.",
        "May",
        "June",
        "July",
        "Aug.",
        "Sept.",
        "Oct.",
        "Nov.",
        "Dec.",
      ],
      dayOfWeek: new Date().getDay(),
      month: new Date().getMonth(),
      day: new Date().getDate(),
      year: new Date().getFullYear(),
    };
  },
};
</script>

<template>
  <time class="dateTimeContainer" :dateTime="`${year}-${month}-${day}`">
    <div class="dateTimeYearAndMonth">
      <span>{{ year }}</span>
      <span>{{ monthEnList[month] }}</span>
    </div>
    <div class="dateTimeDay">{{ day }}</div>
    <div class="dateTimeDayOfWeek">
      <span class="dateTimeDayOfWeekBody">{{ dayOfWeekList[dayOfWeek] }}</span>
      <span class="dateTimeDayOfWeekSuffix">day</span>
    </div>
  </time>
</template>

<style scoped>
.dateTimeContainer {
  display: flex;
  align-items: center;
  gap: calc(0.8rem * 0.2);
}
.dateTimeYearAndMonth {
  display: flex;
  flex-direction: column;
}
.dateTimeYearAndMonth > * {
  font-size: calc(0.8rem * 0.8);
  line-height: 1;
  font-weight: lighter;
}
.dateTimeDay {
  line-height: 1;
  font-size: 1.6rem;
  background: linear-gradient(transparent 30%, rgba(255, 130, 96, 0.8) 45%);
}
.dateTimeDayOfWeek {
  line-height: 1;
  display: flex;
  flex-direction: column;
}
.dateTimeDayOfWeekBody,
.dateTimeDayOfWeekSuffix {
  line-height: 1;
  font-weight: lighter;
  text-transform: uppercase;
  font-size: calc(0.8rem * 0.8);
  display: inline-block;
}
</style>
