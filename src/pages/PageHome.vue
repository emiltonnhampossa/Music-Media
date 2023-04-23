<template>
  <q-page>
    <div class="q-py-lg q-px-md row items-end q-col-gutter-md">
      <div class="col">
        <q-input
        bottom-slots
        v-model="NewTueetContent"
        label="O que estas a Pensar?"
        class="new-tweet"
        counter
        maxlength="280"
        :dense="dense"
        autogrow
        >
        <template v-slot:before>
          <q-avatar size="xl">
            <img src="https://cdn.quasar.dev/img/avatar5.jpg">
          </q-avatar>
        </template>
      </q-input>
      </div>
      <div class="col col-shrink">
        <q-btn
          :disable="!NewTueetContent"
            unelevated
            rounded
            class="q-mb-lg"
            color="primary"
            label="Tweet"
            no-caps
            />
      </div>
    </div>
    <q-separator
    class="divider"
      size="10px"
      color="grey-2" />

      <q-list separator>
      <q-item
        v-for="tweet in tweets"
        :key="tweet.date"
        class="q-py-md">
        <q-item-section avatar top>
          <q-avatar size="xl">
            <img src="https://cdn.quasar.dev/img/avatar5.jpg">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label class="text-subtitle1"><strong>Emilton Nhampossa</strong>
            <span class="text-grey-7">
              @emilton_nhampossa
            </span>
          </q-item-label>
          <q-item-label class="tweet-content text-body1">
            {{ tweet.content }}
          </q-item-label>
          <div class="tweet-icons row justify-between q-mt-sm">
            <q-btn
              flat
              size="sm"
              round
              icon="far fa-comment"
              color="grey"
               />

              <q-btn
              flat
              size="sm"
              round
              icon="fas fa-retweet"
              color="grey"
               />

              <q-btn
              flat
              size="sm"
              round
              icon="far fa-heart"
              color="grey"
              />

              <q-btn
              flat
              size="sm"
              round
              icon="fas fa-trash"
              color="grey" />
          </div>
        </q-item-section>

        <q-item-section side top>
          {{ tweet.date || relativeDate }}
        </q-item-section>
      </q-item>
    </q-list>

  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import { formatDistance} from 'date-fns'

export default defineComponent({
  name: 'PageHome',
  data(){
    return{
      NewTueetContent: '',
      tweets:[
        {
          content:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aspernatur nulla officiis et cum eius. Commodi impedit earum illo enim, itaque vitae autem libero non suscipit eos, corrupti velit laudantium perspiciatis!',
           date:1682272626235
        },
        {
          content:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aspernatur nulla officiis et cum eius. Commodi impedit earum illo enim, itaque vitae autem libero non suscipit eos, corrupti velit laudantium perspiciatis!',
          date:1682272626235
        },

      ]
    }

  },
  filters:{
    relativeDate(value){
      return formatDistance(value, new Date())
    }
  }
})
</script>

<style lang="sass">
.new-tweet
  textarea
  font-size:19px
    line-height: 1.4 !important

  .divider
    border-top:1px solid
      border-bottom:1px solid
        border-color: $grey-2

    .tweet-content
       white-space:pre-line

       .tweet-icons
        margin-left: 5px

</style>
