<script>
import { onMounted } from 'vue';
import { getCurrentInstance } from 'vue';
import { reactive } from 'vue';

export default {
    name:"Card",
    setup(){
    const cards = reactive([
  {
    id: 1,
    name: 'John Doe',
    title: 'Frontend Developer',
    description: 'Specializes in Vue.js and Tailwind CSS.',
    email: 'john@example.com',
    phone: '+1234567890',
    image: 'https://via.placeholder.com/150'
  },
  {
    id: 2,
    name: 'Jane Smith',
    title: 'Backend Developer',
    description: 'Node.js and database expert.',
    email: 'jane@example.com',
    phone: '+9876543210',
    image: 'https://via.placeholder.com/150'
  },
  {
    id: 3,
    name: 'Ali Khan',
    title: 'Full Stack Developer',
    description: 'Works with Vue, Firebase, and Express.',
    email: 'ali@example.com',
    phone: '+1122334455',
    image: 'https://via.placeholder.com/150'
  }
])

const instance=getCurrentInstance()

onMounted(()=>{
    instance.emit("card-event",cards)
})

return{
    cards
}

}
}
</script>
<template>

</template>