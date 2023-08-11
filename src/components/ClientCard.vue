<template>
  <div class="card">
    <div class="card-header">
      <div class="card-status" :style="{ borderColor: clientData.statusColor, color: clientData.statusColor }">
        {{ clientData.status }}
      </div>
      <div class="d-flex align-self-center">
        <div class="card-time d-flex">
          <div> {{ clientData.tasksNextDatetime.split("-").join(".").slice(0, 10) }} </div> 
          <img src="../assets/icons/clock.svg" class="align-self-center">
        </div>
        <div class="card-checkbox align-self-center">
          <input type="checkbox">
        </div>
      </div>
    </div>
    <div class="card-body">
      <div class="card-task-status d-flex">
        <div> {{ clientData.tasksDone }}/{{ clientData.tasksTotal }} </div> <img src="../assets/icons/task.svg">
      </div>
      <div class="card-info-user">
        <div class="card-info-user-name"> {{ clientData.fullName }} </div>
        <div class="card-info-user-about"> {{ clientData.phone }} <span> :Phone </span>  </div>
        <div class="card-info-user-about"> {{ clientData.email }} <span> :Email </span> </div>
        <div class="card-info-user-about"> {{ clientData.channelName }} <span> :Channel </span> </div>
        <div class="card-info-user-about"> {{ clientData.createdAt.split("-").join(".").slice(0, 10) }} <span> :Creation Date </span> </div>
      </div>
    </div>
    <div class="card-footer">
      <div class="card-assignees">
        <div class="card-assignees-number" v-if="assigneData.length - 1"> +{{ assigneData.length - 1 }} </div>
        <img :src="'/src/assets/' + assigneData[assigneData.length - 1]?.image"/>
      </div>
      <div class="card-nav">
        <div class="card-nav-alert">
          <img src="../assets/icons/note.svg">
          <div v-if="clientData.numberOfNotes > 0" class="card-nav-alert-status"> {{ clientData.numberOfNotes }} </div>
        </div>
        <div class="card-nav-alert">
          <img src="../assets/icons/email.svg">
          <div v-if="clientData.numberOfUnreadEmails > 0" class="card-nav-alert-status"> {{ clientData.numberOfUnreadEmails }} </div>
        </div>
        <div class="card-nav-alert">
          <img src="../assets/icons/whatsapp.svg">
          <div v-if="clientData.numberOfUnreadWhatsappMessages > 0" class="card-nav-alert-status"> {{ clientData.numberOfUnreadWhatsappMessages }} </div>
        </div>
        <div class="card-nav-alert">
          <img src="../assets/icons/sms.svg">
          <div v-if="clientData.numberOfUnreadSmsMessages > 0" class="card-nav-alert-status"> {{ clientData.numberOfUnreadSmsMessages }} </div>
        </div>
        <div class="card-nav-alert">
          <img src="../assets/icons/phone.svg">
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from "vue"

interface Client {
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

interface Assigne {
  id: string,
  image: string
}

const props = defineProps<{
  clientData: Client,
  assigneData: (Assigne | undefined)[]
}>()

console.log(props.assigneData)

</script>

<style scoped lang="scss">

.card {
  padding: 15px;
  color: #61758A;
  background-color: #fff;
  box-shadow: 5px 5px 15px gray;
  border-radius: 10px;
  margin: 20px 0;
  width: 400px;
}
.card-header {
  display: flex;
  justify-content: space-between;
  padding-bottom: 15px;
  border-bottom: 1px solid gray;
}

.card-status {
  padding: 5px 15px;
  border: 1px solid;
  font-weight: bold;
  border-radius: 10px;
}

.card-task-status {
  border: 1px solid gray;
  padding: 0 10px;
  border-radius: 5px;
  align-self: baseline;
}

.card-task-status img {
  align-self: center;
  margin-left: 5px;
}

.card-time {
  margin-right: 10px;
  color: #61758A;
}

.card-time img {
  margin-left: 5px;
  align-self: center;
}

input {
  border-color: #BED1DF;
}

.card-body {
  padding-top: 15px;
  display: flex;
  justify-content: space-between;
}

.card-assignees {
  border-radius: 10px;
  display: flex;
}

.card-assignees img {
  width: 37px;
  height: 37px;
  border-radius: 50px;
}

.card-assignees-number {
  padding: 5px;
  border-radius: 25px;
  height: 25px;
  width: 25px;
  text-align: center;
  line-height: 25px;
  border: 1px solid gray;
  margin-right: -5px;
}

.d-flex {
  display: flex;
}

.card-info-user-about {
  margin-top: 10px;
  color: #455568;
}

.card-info-user-about span{
  font-weight: 600;
}

.card-info-user {
  text-align: right;
}

.card-info-user-name {
  font-weight: bold;
  color: #455568;
}

.align-self-center {
  align-self: center;
}

.card-footer {
  margin-top: 25px;
  display: flex;
  justify-content: space-between;
}

.card-nav {
  display: flex;
}

.card-nav-alert {
  position: relative;
  margin: 0 10px;
  cursor: pointer;
}

.card-nav-alert img {
  width: 20px;
  height: 20px;
}


.card-nav-alert-status {
  width: 10px;
  height: 10px;
  text-align: center;
  line-height: 10px;
  font-weight: bold;
  position: absolute;
    top: -10px;
    z-index: 9999999;
    color: #fff;
    right: -7px;
    font-size: 11px;
    background: red;
    padding: 3px;
    border-radius: 10px;
}
</style>