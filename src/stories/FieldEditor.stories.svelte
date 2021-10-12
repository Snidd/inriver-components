<script>
  import { Meta, Template, Story } from "@storybook/addon-svelte-csf";
  import FieldEditor from "../lib/FieldEditor.svelte";
</script>

<!-- More on default export: https://storybook.js.org/docs/react/writing-stories/introduction#default-export -->
<!-- More on argTypes: https://storybook.js.org/docs/svelte/api/argtypes -->
<Meta
  title="Example/FieldEditor"
  component={FieldEditor}
  argTypes={{
    fieldName: { control: "text" },
    fieldValue: { control: "object" },
  }}
/>

<!-- More on component templates: https://storybook.js.org/docs/svelte/writing-stories/introduction#using-args -->
<Template let:args>
  <FieldEditor {...args} />
</Template>

<!-- More on args: https://storybook.js.org/docs/svelte/writing-stories/args -->
<Story
  name="Product Name"
  args={{
    fieldName: "Product name",
    fieldValue: "Test",
  }}
/>

<Story
  name="Length"
  args={{
    fieldName: "Description",
    fieldValue: 23,
  }}
/>

<Story
  name="Locale String EN"
  args={{
    fieldName: "Length",
    fieldValue: { "sv-SE": "Swedish text", en: "English text" },
    language: "en",
  }}
/>
