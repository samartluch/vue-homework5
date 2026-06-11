<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import CourseInfo from './components/CourseInfo.vue'
import StatsSection from './components/StatsSection.vue'
import StudentProfile from './components/StudentProfile.vue'
import AssignmentList from './components/AssignmentList.vue'
import ActivityTimeline from './components/ActivityTimeline.vue'

const studentProfile = ref({
  avatar: 'https://placehold.co/150x150/png?text=AM',
  fullName: 'Alex Morgan',
  email: 'alex.m@edu.com',
  batch: '2026-A',
  track: 'Frontend Development',
})

const courseInfo = ref({
  courseName: 'Frontend Frameworks (Vue 3)',
  instructor: 'Prof. Evans',
  progress: 60,
})

const stats = ref([
  {
    title: 'Lessons Completed',
    value: '12 / 20',
    icon: 'book-open',
  },
  {
    title: 'Exercises Done',
    value: '8 / 10',
    icon: 'check-circle',
  },
  {
    title: 'Current Score',
    value: '92%',
    icon: 'chart-line',
  },
  {
    title: 'Attendance Rate',
    value: '95%',
    icon: 'users',
  },
])

const assignments = ref([
  {
    title: 'Composition API Quiz',
    dueDate: 'June 15',
    status: 'completed',
  },
  {
    title: 'Props Lab Exercise',
    dueDate: 'June 15',
    status: 'pending',
  },
])

const activities = ref([
  {
    activityName: 'Submitted Exercise',
    date: '2 mins ago',
    type: 'submit',
  },
  {
    activityName: 'Quiz Completed',
    date: '1 hour ago',
    type: 'quiz',
  },
  {
    activityName: 'Lab Section Unlocked',
    date: 'Today',
    type: 'unlock',
  },
])
</script>

<template>
  <div class="app-shell">
    <Header
      brand="Vue Lab"
      title="Vue.js Dashboard"
      student-name="Alex Morgan"
    />

    <main class="dashboard" aria-label="Vue props practice dashboard">
      <section class="dashboard__intro">
        <CourseInfo v-bind="courseInfo" />
        <StatsSection :stats="stats" />
      </section>

      <section class="dashboard__workspace" aria-label="Student workspace">
        <StudentProfile v-bind="studentProfile" />
        <AssignmentList :assignments="assignments" />
        <ActivityTimeline :activities="activities" />
      </section>
    </main>

  </div>
</template>
