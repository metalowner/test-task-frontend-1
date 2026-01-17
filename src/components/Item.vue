<<template>
  <div>
    <p>{{ name }}</p>
    <button v-if="!top" @click="emit('add', id)">Add</button>
    <button v-if="top" @click="emit('remove', id)">Remove</button>
  </div>
</template>

<script lang="ts" setup>
// declare item props
const props = defineProps({
    id: {
        type: Number,
        required: true
    },
    name: {
        type: String,
        required: true
    },
    top: {
        type: Boolean,
        required: false
    }
})
// declare emits
const emit = defineEmits(['add', 'remove'])

</script>

<style>

</style>