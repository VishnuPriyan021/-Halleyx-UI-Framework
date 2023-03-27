<template>
  <h1 class="component-heading">Color picker</h1>
  <p class="component-description">
    Custom colours for the web are simple to develop, modify, and experiment
    with with this tool.
  </p>

  <divider :position="'horizontal'" :space="'20px'" />

  <div class="component-example">
    <div class="example-body">
      <colorpalette @customChange="colorValue"></colorpalette>
      <colorpalette
        :highlightcolor="true"
        @customChange="colorValue"
      ></colorpalette>
    </div>
    <div class="example-footer">
      <span class="icon" id="basic-model-icon" @click="showCode('basic-model')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="basic-model" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="basicmodel"
          :read_only="true"
          :theme="editor_theme"
          :languages="[
            ['Javascript', 'Vue'],
            ['javascript', 'JS'],
            ['python', 'Python'],
          ]"
        />
      </div>
    </section>
  </div>

  <divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Select events</h2>
  <hlx-table-v2
    :border="['table', 'header', 'vertical', 'horizontal']"
    :boldHeaders="false"
    :rowHover="false"
    theme="primary"
    :stripedRows="false"
  >
    <template #thead>
      <hlx-table-head v-for="(i, index) in this.alertAttributes" :key="index">{{
        i.label
      }}</hlx-table-head>
    </template>
    <template #tbody>
      <tr v-for="(i, index) in this.table_data" :key="index" id="">
        <hlx-table-cell
          v-for="(j, col_index) in this.alertAttributes"
          :align="'left'"
          :key="col_index"
        >
          {{ i[j.prop] }}
        </hlx-table-cell>
      </tr>
    </template>
  </hlx-table-v2>
  <!-- <hlx-table
    :data="this.select_events"
    :border="true"
    theme="secondary"
    :rowHover="true"
    :bold_header="true"
  >
    <hlx-column :prop="'Name'" :label="'Name'" :type="'string'" />
    <hlx-column
      :prop="'Description'"
      :label="'Description'"
      :type="'string'"
      :width="400"
    />
    <hlx-column :prop="'Parameters'" :label="'Parameters'" :type="'string'" />
  </hlx-table> -->
  <!-- <hlx-table-component :tableData="this.data.table_data" :theader="this.data.columns" :border="true"/>    -->
</template>
<script>

import hlxTableV2 from "../components/table-v2/HlxTableV2.vue";
import hlxTableHead from "../components/table-v2/HlxTableHead.vue";
import hlxTableCell from "../components/table-v2/HlxTableCell.vue";
// import hlxTable from "../components/NewTable.vue";
import CodeEditor from "simple-code-editor";
// import hlxColumn from "../components/NewTableColumn.vue";
import divider from "../components/DividerComponent.vue";
import colorpalette from "../components/ColorpaletteComponent.vue";
export default {
  components: {
    divider,
    colorpalette,
    // hlxTable,
    CodeEditor,
    // hlxColumn,
    hlxTableCell,
    hlxTableHead,
    hlxTableV2,
  },
  data() {
    return {
      editor_theme: "light",
       alertAttributes: [
        {
          prop: "name",
          label: "Attributes",
          width: "50",
          type: "string",
          format: "",
        },
        {
          prop: "description",
          label: "Description",
          width: "50",
          type: "string",
          format: "",
        },
        {
          prop: "parameters",
          label: "Parameters",
          width: "50",
          type: "string",
          format: "",
        },
      ],
      table_data: [
        {
          name: "customChange",
          description: "Return the selected color values",
          parameters: "-",
        },
      ],
      // select_events: [
      //   {
      //     Name: "customChange",
      //     Description: "Return the selected color values",
      //     Parameters: "-",
      //   },
      // ],
      colorvalue: "",
      basicmodel: `
      <template>
      <hlx-colorpalette @customChange="colorValue"></hlx-colorpalette>
      <hlx-colorpalette :highlightcolor="true" @customChange="colorValue"></hlx-colorpalette>
      </template>
`
    };
  },
  methods: {
    colorValue(value) {
      this.colorvalue = value;
      console.log(this.colorvalue,'Colorvalue');
    },
    showCode(val) {
      document.getElementById(val + "-icon").classList.toggle("active-icon");
      if (document.getElementById(val).style.display === "none") {
        document.getElementById(val).style.display = "block";
      } else if (document.getElementById(val).style.display === "block") {
        document.getElementById(val).style.display = "none";
      }
    },
  },
};
</script>

<style scoped>
.example-body {
  overflow: visible;
}
</style>
