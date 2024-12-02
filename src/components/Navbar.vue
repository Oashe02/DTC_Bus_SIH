<template>
  <nav class="navbar">
    <div class="container">
      <div class="navbar-content">
        

        <!-- Logo and Title -->
        <div class="logo">
          <div class="logo-icon">
            <Bus class="icon" />
          </div>
          <span class="logo-title">DTC Driver Portal</span>
        </div>

        <!-- Right side (Notification, Settings, Profile) -->
        <div class="right-side">
          <!-- Notifications Bell -->
          <button class="notification-button" @click="toggleNotifications">
            <Bell class="icon-small" />
            <span v-if="hasUnreadNotifications" class="notification-dot"></span>
          </button>

          <!-- Settings Button -->
          <button class="settings-button" @click="openSettings">
            <Settings class="icon-small" />
          </button>

          <!-- Profile Dropdown -->
          <div class="profile-dropdown">
            <div class="profile-info">
              <p class="profile-name">XYZABC</p>
              <p class="profile-id">Driver #4872</p>
            </div>
            <div class="profile-image" @click="toggleProfileMenu">
              <img
                src="https://images.unsplash.com/photo-1633332755192-727a05c4013d?w=400"
                alt="Driver profile"
                class="image"
              />
            </div>
            <!-- Profile Dropdown Menu -->
            <div v-if="isProfileMenuOpen" class="profile-menu">
              <p class="profile-name">Rajesh Kumar</p>
              <p class="profile-id">Driver #4872</p>
              <div>
                <button @click="logout" class="logout-button">
                  Log Out
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Settings Modal -->
    <div v-if="isSettingsOpen" class="settings-modal">
      <div class="settings-content">
        <h3 class="settings-title">Settings</h3>
        <button class="close-settings" @click="closeSettings">Close Settings</button>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Bus, Bell, Settings, LogOut } from 'lucide-vue-next';

// State for unread notifications
const hasUnreadNotifications = ref(true);

// State for settings modal and profile dropdown
const isSettingsOpen = ref(false);
const isProfileMenuOpen = ref(false);

// State for sidebar toggle
const isSidebarOpen = ref(false);

// Toggle notification state
const toggleNotifications = () => {
  hasUnreadNotifications.value = !hasUnreadNotifications.value;
  if (hasUnreadNotifications.value) {
    alert('You have new notifications!');
  } else {
    alert('All notifications are read.');
  }
};

// Open settings modal
const openSettings = () => {
  isSettingsOpen.value = true;
};

// Close settings modal
const closeSettings = () => {
  isSettingsOpen.value = false;
};

// Toggle profile menu
const toggleProfileMenu = () => {
  isProfileMenuOpen.value = !isProfileMenuOpen.value;
};

// Log out
const logout = () => {
  alert('You have logged out!');
};

// Toggle sidebar visibility
const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};
</script>

<style scoped>
/* Combined Navbar styles */
.navbar {
  background: linear-gradient(to right, #1e3a8a, #1d4ed8); /* from-blue-800 to-blue-900 */
  color: white;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px, rgba(0, 0, 0, 0.1) 0px 1px 3px;
  margin-bottom: 0;
}

/* Container for navbar content */
.container {
  max-width: 7xl;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Main navbar content, flexbox layout */
.navbar-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 4rem;
}

/* Toggle button (Hamburger) */
.toggle-button {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 2rem;
  height: 1.25rem;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  margin-right: 1rem;
}

.toggle-icon {
  width: 100%;
  height: 2px;
  background-color: white;
  transition: all 0.3s ease;
}

/* Logo section */
.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.logo-icon {
  background-color: rgba(255, 255, 255, 0.1);
  padding: 0.5rem;
  border-radius: 0.375rem;
}

.logo-title {
  font-weight: bold;
  font-size: 1.25rem;
}

/* Right side (Notification, Settings, Profile) */
.right-side {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

/* Notification button */
.notification-button {
  padding: 0.5rem;
  border-radius: 9999px;
  background: transparent;
  cursor: pointer;
  position: relative;
}

.notification-button:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.notification-dot {
  position: absolute;
  top: 0;
  right: 0;
  height: 0.5rem;
  width: 0.5rem;
  background-color: #f56565;
  border-radius: 9999px;
}

/* Settings button */
.settings-button {
  padding: 0.5rem;
  border-radius: 9999px;
  background: transparent;
  cursor: pointer;
}

.settings-button:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

/* Profile dropdown */
.profile-dropdown {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  border-left: 1px solid rgba(255, 255, 255, 0.2);
  padding-left: 1.5rem;
  position: relative;
}

.profile-info {
  text-align: right;
}

.profile-name {
  font-weight: 500;
}

.profile-id {
  font-size: 0.875rem;
  color: rgba(59, 130, 246, 0.75);
}

.profile-image {
  width: 2.5rem;
  height: 2.5rem;
  overflow: hidden;
  border-radius: 9999px;
  cursor: pointer;
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Profile dropdown menu */
.profile-menu {
  position: absolute;
  top: 100%;
  right: 0;
  background-color: white;
  color: black;
  padding: 1rem;
  border-radius: 0.375rem;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px, rgba(0, 0, 0, 0.1) 0px 1px 3px;
  width: 10rem;
}

.profile-menu button {
  width: 100%;
  text-align: left;
  color: #f56565;
}

/* Settings modal */
.settings-modal {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.settings-content {
  background-color: white;
  padding: 2rem;
  border-radius: 0.375rem;
  max-width: 28rem;
  width: 100%;
}

.settings-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.close-settings {
  background-color: #f56565;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  cursor: pointer;
}

/* For logout button in settings */
.logout-button {
  color: #f56565;
  font-size: 0.875rem;
  text-align: left;
}

/* Prevent wrapping on smaller screens */
@media (max-width: 768px) {
  .navbar-content {
    flex-wrap: wrap;
  }
}
</style>
