<template>
  <b-navbar>
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
          alt="Lightweight UI components for Vue.js based on Bulma"
        />
      </b-navbar-item>
    </template>
    <template slot="start">
      <b-navbar-item>
        <router-link to="sports">Sports</router-link>
      </b-navbar-item>
      <b-navbar-item>
        <router-link to="politics">Politics</router-link>
      </b-navbar-item>
      <b-navbar-item>
        <router-link to="/bussiness">Bussiness</router-link>
      </b-navbar-item>
      <b-navbar-item>
        <router-link to="/science">Science</router-link>
      </b-navbar-item>
      <b-navbar-item>
        <router-link to="/health">Health</router-link>
      </b-navbar-item>
    </template>
    <template slot="end">
      <b-navbar-item tag="div">
        <b-field>
          <b-input placeholder="Search..." type="search" icon="magnify"></b-input>
          <p class="control">
            <button class="button is-primary">Search</button>
          </p>
        </b-field>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>