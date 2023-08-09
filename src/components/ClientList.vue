<template>
    <div>
        <ClientCard v-for="client in props.clientsData" :clientData="client" :assigneData="returnAssignees(client, assigneesData)" />
    </div>
</template>

<script setup lang="ts">
import { defineProps } from "vue";
import ClientCard from "./ClientCard.vue";

interface Clients {
  id: string,
  assignees: string[],
  channelName: string,
  createdAt: string,
  email: string,
  fullName: string,
  tasksDone: number,
  tasksTotal: number,
  numberOfNotes: number,
  numberOfUnreadEmails: number,
  numberOfUnreadSmsMessages: number,
  numberOfUnreadWhatsappMessages: number,
  phone: string,
  status: string,
  statusColor: string,
  tasksNextDatetime: string  
}

interface Assignees {
  id: string,
  image: string
}

const props = defineProps<{
    clientsData: Clients[],
    assigneesData: Assignees[]
}>()

function returnAssignees(client: { assignees: string[]; }, assignees: Assignees[]) {
    let sortAssignees: (Assignees | undefined)[] = []
    client.assignees.forEach((element: string) => {
        sortAssignees.push(assignees.find(el => el.id == element))
    });
    return sortAssignees;
}

</script>

<style lang="scss" scoped>

</style>