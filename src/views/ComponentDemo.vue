<template>
  <div>
    <h1>
      this is component test page that implements basic chat
    </h1>
    <div>
      <ul>
        <li 
          v-for="(message, index) in messages"
          :key="message.body + index"
        >
          person {{message.senderId}} says {{message.body}}
        </li>
      </ul>
    </div>
    <div>
      <div>
        <form v-on:submit.prevent="sendMessage(1)">
          <label for="person1input">person 1:</label>
          <input
            id="person1input"
            type="text"
            v-model="messageInput1"
          >
          <button type="submit">გაგზავნა</button>
        </form>
      </div>
      <div>
        <form v-on:submit.prevent="sendMessage(2)">
          <label for="person2input">person 2:</label>
          <input 
            id="person2input"
            type="text"
            v-model="messageInput2"
          >
          <button type="submit">გაგზავნა</button>
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

<style>

</style>