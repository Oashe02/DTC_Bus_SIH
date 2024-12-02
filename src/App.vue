<template>
  <q-layout view="lHh lpR">
    <!-- Navbar Component -->
    <q-header elevated>
      <Navbar />
    </q-header>
    
    <q-page-container>
      <q-page padding>
        <div class="q-pa-md">
          <!-- Upcoming Schedule Section -->
          <UpcomingSchedule />
          
          <QuickStats />

          <!-- Main Content Grid -->
          <q-row class="q-gutter-md" :cols="1" :lg="3">
            <!-- Left Column - Schedule Section -->
            <q-col :span="12" :lg="8" class="order-lg-1">
              <q-card class="q-mb-md">
                <q-card-section>
                  <WeatherWidget />
                </q-card-section>
                <q-card-section>
                  <TimeTable />
                </q-card-section>
              </q-card>
            </q-col>

            <!-- Right Column - Weekly Overview -->
            <q-col :span="12" :lg="4" class="order-lg-2">
              <q-card class="q-mb-md">
                <q-card-section>
                  <WeeklySchedule />
                </q-card-section>
              </q-card>
            </q-col>
          </q-row>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import Navbar from './components/Navbar.vue'
import WeatherWidget from './components/WeatherWidget.vue'
import TimeTable from './components/TimeTable.vue'
import WeeklySchedule from './components/WeeklySchedule.vue'
import QuickStats from './components/QuickStats.vue'
import UpcomingSchedule from './components/UpcomingSchedule.vue'
</script>

<style scoped>
/* Custom styles for Quasar components can go here */
</style>
