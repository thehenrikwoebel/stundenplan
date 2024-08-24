<template>
  <v-app>
    <v-main id="grid">
      <Card fach="Deutsch" class="montag" style="grid-row: 1;"></Card>
      <Card fach="Mathe" class="montag" style="grid-row: 2;"></Card>
      <Card fach="Englisch" class="montag" style="grid-row: 3;"></Card>
      <Card fach="Chemie" class="montag" style="grid-row: 4;"></Card>
      <Card fach="" class="montag" style="grid-row: 5;"></Card>
      <Card fach="" class="montag" style="grid-row: 6;"></Card>
      <Card fach="Physik" class="montag" style="grid-row: 7;"></Card>
      <Card fach="Physik" class="montag" style="grid-row: 8;"></Card>

      <Card fach="Deutsch" class="dienstag" style="grid-row: 1;"></Card>
      <Card fach="Deutsch" class="dienstag" style="grid-row: 2;"></Card>
      <Card fach="Mathe" class="dienstag" style="grid-row: 3;"></Card>
      <Card fach="Mathe" class="dienstag" style="grid-row: 4;"></Card>
      <Card fach="Chemie" class="dienstag" style="grid-row: 5;"></Card>
      <Card fach="Chemie" class="dienstag" style="grid-row: 6;"></Card>
      <Card :fach="dienstag()" class="dienstag" style="grid-row: 7;"></Card>
      <Card :fach="dienstag()" class="dienstag" style="grid-row: 8;"></Card>

      <Card fach="Physik" class="mittwoch" style="grid-row: 1;"></Card>
      <Card fach="Physik" class="mittwoch" style="grid-row: 2;"></Card>
      <Card fach="" class="mittwoch" style="grid-row: 3;"></Card>
      <Card fach="" class="mittwoch" style="grid-row: 4;"></Card>
      <Card fach="" class="mittwoch" style="grid-row: 5;"></Card>
      <Card fach="" class="mittwoch" style="grid-row: 6;"></Card>
      <Card :fach="mittwoch()" class="mittwoch" style="grid-row: 7;"></Card>
      <Card :fach="mittwoch()" class="mittwoch" style="grid-row: 8;"></Card>

      <Card fach="Englisch" class="donnerstag" style="grid-row: 1;"></Card>
      <Card fach="Informatik" class="donnerstag" style="grid-row: 2;"></Card>
      <Card fach="Erdkunde" class="donnerstag" style="grid-row: 3;"></Card>
      <Card fach="Erdkunde" class="donnerstag" style="grid-row: 4;"></Card>
      <Card fach="Mathe" class="donnerstag" style="grid-row: 5;"></Card>
      <Card fach="Mathe" class="donnerstag" style="grid-row: 6;"></Card>
      <Card :fach="donnerstag()" class="donnerstag" style="grid-row: 7;"></Card>
      <Card :fach="donnerstag()" class="donnerstag" style="grid-row: 8;"></Card>

      <Card fach="Physik" class="freitag" style="grid-row: 1;"></Card>
      <Card fach="Physik" class="freitag" style="grid-row: 2;"></Card>
      <Card fach="Informatik" class="freitag" style="grid-row: 3;"></Card>
      <Card fach="Informatik" class="freitag" style="grid-row: 4;"></Card>
      <Card fach="Sport" class="freitag" style="grid-row: 5;"></Card>
      <Card fach="Sport" class="freitag" style="grid-row: 6;"></Card>
      <Card fach="" class="freitag" style="grid-row: 7;"></Card>
      <Card fach="" class="freitag" style="grid-row: 8;"></Card>
    </v-main>
  </v-app>
</template>

<script>
import Card from "@/components/Card.vue";
  export default {
    name: 'app',
    components: {
      Card
    },
    data: () => ({
      getDateWeek(date) {
        const currentDate = 
            (typeof date === 'object') ? date : new Date();
        const januaryFirst = 
            new Date(currentDate.getFullYear(), 0, 1);
        const daysToNextMonday = 
            (januaryFirst.getDay() === 1) ? 0 : 
            (7 - januaryFirst.getDay()) % 7;
        const nextMonday = 
            new Date(currentDate.getFullYear(), 0, 
            januaryFirst.getDate() + daysToNextMonday);
    
        return (currentDate < nextMonday) ? 52 : 
        (currentDate > nextMonday ? Math.ceil(
        (currentDate - nextMonday) / (24 * 3600 * 1000) / 7) : 1);
      },
      woche(fachGerade, fachUnGerade) {
        return this.getDateWeek() % 2 === 0 ? fachGerade : fachUnGerade;
      },
      dienstag() {
        return this.woche("Erdkunde", "Sport");
      },
      mittwoch() {
        return this.woche("Geschichte", "Englisch");
      },
      donnerstag() {
        return this.woche("", "Geschichte");
      },
    })
  }
</script>

<style scoped>
  #grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(8, 1fr);
    grid-auto-flow: row;
  }
  .montag {
    grid-column: 1;
  }
  .dienstag {
    grid-column: 2;
  }
  .mittwoch {
    grid-column: 3;
  }
  .donnerstag {
    grid-column: 4;
  }
  .freitag {
    grid-column: 5;
  }
</style>