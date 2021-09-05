<script>
    export let courseGoal;
    export let ifRed;

   $: ifRed = courseGoal.indexOf('!')>-1;
    
</script>

<style>
    .red {
      color: red;
    }
  </style>

<h1 class="output" class:red="{ifRed}">{courseGoal}</h1>