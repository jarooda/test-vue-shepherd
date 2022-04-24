<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p
      v-for="num in 15"
      :key="num"
      :id="'num-' + num"
      class="my-3"
    >Hello I am ID {{ num }}</p>
  </div>
</template>

<script>
import Shepherd from 'shepherd.js';

export default {
  name: 'AboutShepherd',
  mounted() {
    this.$nextTick(() => {
      const tour = new Shepherd.Tour({
        useModalOverlay: true,
      });

      tour.addSteps([
        {
          modalOverlayOpeningRadius: 20,
          modalOverlayOpeningPadding: 20,
          attachTo: { element: '#num-1', on: 'bottom' },
          text: `
          <div class="d-flex border coachmark-testing__wrapper">
            <img src="https://cdn.worldvectorlogo.com/logos/vue-9.svg" class="coachmark-testing__icon" alt="testing">
            <div>
              <h5>Title</h5>
              <p>This is description</p>
            </div>
          </div>
          <p class="coachmark-testing__steps">1 of 3</p>
          `,
          buttons: [
            {
              text: 'Next',
              action: tour.next,
              classes: 'coachmark-testing__next'
            }
          ],
          cancelIcon: {
            enabled: true
          }
        },
        {
          attachTo: { element: '#num-4', on: 'top' },
          text: `
          <div class="d-flex border coachmark-testing__wrapper">
            <img src="https://cdn.worldvectorlogo.com/logos/vue-9.svg" class="coachmark-testing__icon" alt="testing">
            <div>
              <h5>Title</h5>
              <p>This is description</p>
            </div>
          </div>
          <p class="coachmark-testing__steps">2 of 3</p>
          `,
          buttons: [
            {
              text: '<',
              action: tour.back,
              classes: 'coachmark-testing__back'
            },
            {
              text: 'Next',
              action: tour.next,
              classes: 'coachmark-testing__next'
            }
          ],
          cancelIcon: {
            enabled: true
          }
        },
        {
          attachTo: { element: '#num-9', on: 'top' },
          text: `
          <div class="d-flex border coachmark-testing__wrapper">
            <img src="https://cdn.worldvectorlogo.com/logos/vue-9.svg" class="coachmark-testing__icon" alt="testing">
            <div>
              <h5>Title</h5>
              <p>This is description</p>
            </div>
          </div>
          <p class="coachmark-testing__steps">3 of 3</p>
          `,
          buttons: [
            {
              text: '<',
              action: tour.back,
              classes: 'coachmark-testing__back'
            },
            {
              text: 'Complete',
              action: tour.complete,
              classes: 'coachmark-testing__next'
            }
          ],
          cancelIcon: {
            enabled: true
          }
        }
      ]);

      tour.start();
    });
  }
}
</script>

<style>
@import '~shepherd.js/dist/css/shepherd.css';

.shepherd-element[data-popper-placement^="right"] {
  left: 27px !important;
}

.shepherd-element[data-popper-placement^="bottom"] {
  top: 27px !important;
}

.shepherd-element[data-popper-placement^="left"] {
  right: 27px !important;
}

.shepherd-element[data-popper-placement^="top"] {
  bottom: 27px !important;
}

.coachmark-testing__icon {
  width: 64px;
  height: 64px;
}

.coachmark-testing__steps {
  max-width: 100px;
  word-wrap: normal;
  position: relative;
  bottom: -43px;
}

.coachmark-testing__next {
  color: white;
  background: #2325B3;
  border-radius: 48px;
  padding: 6px 16px;
  width: 148px;
  height: 36px;
}

.coachmark-testing__back {
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  color: #2325B3;
  border: #2325B3 1px solid;
  border-radius: 40px;
}
</style>
