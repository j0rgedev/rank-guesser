<script setup>
  const emit = defineEmits(['selected-rank']);

  const { rank, isDisabled } = defineProps({
    rank: {
      type: String,
      required: true
    },
    isDisabled: {
      type: Boolean,
      default: false
    }
  })

  const toggleSelected = (buttonRef) => {
    if(buttonRef.classList.contains('selected')){
      buttonRef.classList.remove('selected');
      emit('selected-rank', '');
    } else {
      buttonRef.classList.add('selected');
      emit('selected-rank', rank, buttonRef);
    }
  }
</script>

<template>
  <div class="rank__button">
    <button class="valorant-font" type="button" :disabled="isDisabled" @click="toggleSelected($event.target)">{{ rank }}</button>
  </div>
</template>

<style>
  .rank__button {
    min-width: 100px;
    width: fit-content;
    height: 50px;
  }

  .rank__button button.selected {
    background-color: var(--color-bg-rank-button-hover);
    color: var(--color-rank-button-selected);
    border-color: var(--color-bg-rank-button-hover);
  }

  .rank__button button.selected:hover {
    background-color: var(--color-bg-rank-button-hover);
    border-color: var(--color-bg-rank-button-hover);
  }

  .rank__button button {
    width: 100%;
    height: 100%;
    min-width: 114px;
    font-size: clamp(12px, 1.5vw, 26px);
    padding: 0 18px;
    color: var(--color-text);
    border: 1px solid rgba(232,234,237, .4);
    border-radius: 20px;
    background-color: transparent;
    cursor: pointer;
    transition: all .1s ease-in-out;
  }

  .rank__button button:hover {
    background-color: var(--color-rank-button-hover);
    border-color: var(--color-rank-button-hover);
  }

  .rank__button button:active {
    transform: scale(.95);
  }

  .rank__button button:disabled {
    opacity: .5;
    cursor: not-allowed;
  }

  .rank__button button:disabled:hover {
    background-color: transparent;
    border-color: rgba(232,234,237, .4);
  }

  .rank__button button:disabled:active {
    transform: none;
  }

  @media screen and (max-width: 768px) {
    .rank__button button {
      padding: 0 8px;
      min-width: 84px;
    }
  }
</style>