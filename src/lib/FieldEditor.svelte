<script lang="ts">
  export let name: string;
  export let value:
    | Record<string, string>
    | string[]
    | string
    | number
    | undefined;

  export let language: string = "en";
  
  if (typeof value === "string") {
    value = value;
  } else if (typeof value === "number") {
    value = value.toString();
  } else if (value === undefined) {
    value = "";
  }
  console.log(value);
</script>

<div class="wrapper">
  <fieldset>
    <div class="flexchildren">
      <p class="fieldname"><span class="label">{name}</span></p>
      <div class="fieldvalue">
        {#if typeof value === "string"}
          <input class="value" bind:value />
        {/if}
        {#if Array.isArray(value)}
          <input class="value" value={value.join(";")}/>
        {/if}
        {#if value.hasOwnProperty(language)}
        <input class="value" bind:value={value[language]} />
        {/if}
      </div>
    </div>
  </fieldset>
</div>

<style>
  :root {
    font-family: "Nunito Sans", Helvetica, Arial, sans-serif;
    line-height: 21px;
    font-size: 14px;
  }
  fieldset {
    margin: 0;
    padding: 0;
    border: 0px;
  }

  .fieldvalue {
    flex: 1 1 0%;
  }

  .value {
    width: calc(100% - 30px);
    display: block;
    padding: 4px 8px;
    height: 18px;
    border: 1px solid #ddd;
    border-radius: 2px;
    --transition-fast: all 0.2s;
    --transition-medium: all 0.4s;
  }

  .wrapper {
    display: block;
    margin-top: 0;
    margin-bottom: 16px;
    border-bottom: 1px solid #ddd;
    padding-bottom: 16px;
  }

  .label {
    font-weight: 700;
  }

  .fieldname {
    margin: 0 36px 0 19px;
    padding: 4px;
    width: 250px;
    align-items: normal;
    justify-content: normal;
  }

  .flexchildren {
    display: flex;
  }
</style>
