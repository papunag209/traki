<template>
  <div>
    <h1>
      this is component test page that implements basic chat
    </h1>
    <div class="message-window-wrapper">
      <ul class="messages-list">
        <li
          v-for="(message, index) in messages"
          :key="message.body + index"
          v-bind:class="{
            'flex-container flex-justify-right ': message.senderId === 1,
            'flex-container .message-window-wrapper ': message.senderId === 2,
          }"
        >
          <div class="message-wrapper">
            <div class="message-sender-id">
              sender is: {{message.senderId}}
            </div>
            <div>
              {{message.body}}
            </div>
          </div>

        </li>
      </ul>
    </div>
    <div class="inputs">
      <div class="person-input-1">
        <form v-on:submit.prevent="sendMessage(1)">
          <label for="person1input">person 1:</label>
          <input
            id="person1input"
            type="text"
            v-model="messageInput1"
          >
          <button type="submit" >gagzavna</button>
        </form>
      </div>
      <div class="person-input-2">
        <form v-on:submit.prevent="sendMessage(2)">
          <label for="person2input">person 2:</label>
          <input 
            id="person2input"
            type="text"
            v-model="messageInput2"
          >
          <button type="submit">gagzavna</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComponentDemo',
  data: function () {
    return {
      messageInput1: '',
      messageInput2: '',
      messages: []
    }
  },
  methods: {
    sendMessage (senderId) {
      console.log('message sent by user id: ' + senderId)
      if (senderId === 1) {
        this.messages.push({
          senderId: senderId,
          body: this.messageInput1,
        })
        this.messageInput1 = ''
      } else if (senderId === 2) {
        this.messages.push({
          senderId: senderId,
          body: this.messageInput2,
        })
        this.messageInput2 = ''
      }
    }
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  
}

.flex-container {
  display: flex;
  padding: 9px;
}

.flex-justify-right {
  justify-content: flex-end;
}

.is-message-1 {
  background-color: rgb(201, 66, 255);
}

.is-message-1 .message-wrapper .message-sender-id {
  background-color: green;
}

.message-window-wrapper {
  background-color: rgb(99, 245, 221);
  width: 780px;
  height: 544px;
  margin: auto;
  border-radius: 15px;
}


</style>