<script>
    export let redOrNot;
    export let goal;
    
</script>

<style>
    .red {
      color: red;
    }
  </style>

<h1 class="output" class:red="{redOrNot}">{goal}</h1>