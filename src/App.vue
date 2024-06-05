<template>
  <div>
    <the-header></the-header>
    <!-- <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>
    <course-goal #default="slotprops">
        <h2>{{ slotprops.item }}</h2>
        <p>{{ slotprops["another-prop"] }}</p>
    </course-goal> -->
    <button @click="selectedComponent('active-goal')">Active Goal</button>
    <button @click="selectedComponent('manage-goal')">Manage Goal</button>
    <!-- <active-goal v-if="selectedGoal === 'active-goal'"></active-goal>
    <manage-goal v-if="selectedGoal === 'manage-goal'"></manage-goal> -->
    <keep-alive>
      <component :is="selectedGoal"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from "./components/Layout/TheHeader.vue";
// import BadgeList from "./components/BadgeList.vue";
// import UserInfo from "./components/UserInfo.vue";
// import CourseGoal from "./components/CourseGoal.vue";
import ActiveGoal from "./components/ActiveGoal.vue";
import ManageGoal from "./components/ManageGoal.vue";

export default {
  components: {
    "the-header": TheHeader,
    // BadgeList,
    // UserInfo,
    // CourseGoal,
    ActiveGoal,
    ManageGoal,
  },
  data() {
    return {
      activeUser: {
        name: "Maximilian Schwarzmüller",
        description: "Site owner and admin",
        role: "admin",
      },
      selectedGoal: "active-goal",
    };
  },
  methods: {
    selectedComponent(comp) {
      this.selectedGoal = comp;
    },
  },
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
