<template>
  <div class="details">
    <div class="general-informations">
      <div class="city-name">{{ name }}</div>
      <div class="city-temp">
        <fa
          v-if="$parent.show(desc) === 'sun'"
          icon="sun"
          size="7x"
          :style="{ color: '#FFF' }"
        />
        <fa
          v-if="$parent.show(desc) === 'rain'"
          icon="cloud-rain"
          size="7x"
          :style="{ color: '#FFF' }"
        />
        <fa
          v-if="$parent.show(desc) === 'clouds'"
          icon="cloud"
          size="7x"
          :style="{ color: '#FFF' }"
        />
        <fa
          v-if="$parent.show(desc) === 'snow'"
          icon="snowflake"
          size="4x"
          :style="{ color: 'rgb(182, 204, 255)' }"
        />
        <div class="temp-value">{{ $parent.caclculateCelsius(temp) }}°C</div>
      </div>
      <div class="short-desc">{{ desc }}</div>
      <div class="last-update">
        Last update <b>{{ $parent.lastUpdate }}</b>
      </div>
    </div>
    <div class="weather-props">
      <div>
        <fa
          icon="temperature-full"
          size="1x"
          :style="{
            color: '#FFF',
          }"
        />
        {{
          $parent.caclculateCelsius($parent.currentWeather.main.feels_like)
        }}°C (Feels like)
      </div>
      <div>
        <fa
          icon="angles-down"
          size="1x"
          :style="{
            color: '#FFF',
          }"
        />
        {{ $parent.currentWeather.main.pressure }} hPa
      </div>
      <div>
        <fa
          icon="wind"
          size="1x"
          :style="{
            color: '#FFF',
          }"
        />
        {{ $parent.currentWeather.wind.speed }} m/s
      </div>
      <div>
        <fa
          icon="droplet"
          size="1x"
          :style="{
            color: '#FFF',
          }"
        />
        {{ $parent.currentWeather.main.humidity }}%
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineProps, withDefaults } from "vue-class-component";

interface Props {
  name: string;
  temp: number;
  desc: string;
}

const props = withDefaults(defineProps<Props>(), {
  name: "Example",
  temp: 0,
  desc: "Text",
});
</script>

<script lang="ts">
import { Vue } from "vue-class-component";
export default class CityDetails extends Vue {}
</script>
