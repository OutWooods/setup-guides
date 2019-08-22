1. Vuex Structure

state: {
  message: '',
},
getters: {
  message: (state) => {
    return state.message
  },
},
mutations: {
  SET_MESSAGE: (state, newValue) => {
    state.message = newValue
  // other mutations
},
actions: {
  setMessage: ({commit, state}, newValue) => {
    commit('SET_MESSAGE', newValue)
    return state.message
  },
}

(to call actions you use dispatch)

2. To access vuex in a component
 this.$store.

