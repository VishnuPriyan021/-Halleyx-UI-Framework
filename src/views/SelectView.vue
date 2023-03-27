<template>
<!-- {{this.data.key}}
{{this.data}} -->

  <h1 class="component-heading">Select</h1>
  <p class="component-description">
    Using a drop-down menu instead of the native element is a classy
    improvement.
  </p>
  <divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Basic usage</h2>

  <p class="component-description">
    To specify input for the dropdown<b> :options</b><br />
    To display custom placeholder, add <b>:placeholder_value</b> attribute which
    takes in a string value <br />
    You can also toggle label animation to On/Off by setting
    <b>:label_animation</b> attribute to <b>true</b> To clear the selected value
    use <b>:clearable</b> to <b>true</b><br />
    The selected value can be accessed from the <b>v-model:value</b> attribute<br>
    The selected name can be accessed from the <b>v-model:name</b> attribute<br>
    Pre-populate the select with value of the option using the :prevalue attribute 
  </p>
  <div class="component-example">
    <div class="example-body">
      <hlxselect
        :options="this.dropdown_data"
        :placeholder_value="'Language'"
        :labelanimation="true"
         v-model:value ="this.data.key"
        :clearable="true"
        :prevalue="this.prevalue"
      ></hlxselect>
    </div>
    <div class="example-footer">
      <span
        class="icon"
        id="basic-select-icon"
        @click="showCode('basic-select')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="basic-select" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="basic_select"
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
  <h2 class="component-side-heading">Select with icons</h2>

  <p class="component-description">
    To have icon inside the select refer the table below<br />
    To specify input for the dropdown<b> :options</b><br />
    To display custom placeholder, add <b>:placeholder_value</b> attribute which
    takes in a string value <br />
    You can also toggle label animation to On/Off by setting
    <b>:label_animation</b> attribute to <b>true</b> To clear the selected value
    use <b>:clearable</b> to <b>true</b><br />
    To add country flag inside the select use <b>:icon</b> to <b>true</b>
  </p>
  <div class="component-example">
    <div class="example-body">
      <hlxselect
        :options="this.new_data"
        :placeholder_value="'CountryFlag'"
        :labelanimation="true"
        :icon="true"
        @customChange="selectValue"
      ></hlxselect>
      <!-- <hlxselect :options="this.dropdown_data" :placeholder_value="'hello'" :labelanimation="true" :clearable="true"  @customChange="selectValue"></hlxselect> -->
    </div>
    <div class="example-footer">
      <span
        class="icon"
        id="basic-country-select-icon"
        @click="showCode('basic-country-select')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="basic-country-select" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="basic_country_select"
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

  <h1 class="component-heading">Multiple select with search</h1>

  <p class="component-description">
    To enable multi-select use <b>:multi_select</b> to <b>true</b><br />
    To specify input for the dropdown<b> :multiselect_options</b><br />
    You can also toggle label animation to On/Off by setting
    <b>:label_animation</b> attribute to <b>true</b>
  </p>
  <div class="component-example">
    <div class="example-body">
      <hlxselect
        :multiselect_options="this.dropdown_data1"
        :multi_select="true"
        :placeholder_value="'Language'"
        :labelanimation="true"
        v-model:value ="this.check"
        @customChange="selectValue"
      ></hlxselect>
      <!-- <hlxselect :multiselect_options="this.dropdown_data1" :multi_select="true" :filter_select="true" :placeholder_value="'Name'" :labelanimation="true" @customChange ="selectValue" ></hlxselect> -->
    </div>
    <div class="example-footer">
      <span
        class="icon"
        id="basic-multiselect-icon"
        @click="showCode('basic-multiselect')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="basic-multiselect" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="basic_multiselect"
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

  <h1 class="component-heading">Multiple select for filter</h1>

  <p class="component-description">
    To enable multi-select use <b>:multi_select</b> to <b>true</b> and to enable
    cascade filter enable the <b>filter_select</b> to <b>true</b><br />
    To specify input for the dropdown<b> :multiselect_options</b><br />
    You can also toggle label animation to On/Off by setting
    <b>:label_animation</b> attribute to <b>true</b>
  </p>
  <div class="component-example">
    <div class="example-body">
      <!-- <hlxselect :multiselect_options="this.dropdown_data1" :multi_select="true" :placeholder_value="'Name'" :labelanimation="true" @customChange ="selectValue" ></hlxselect> -->
      <hlxselect
        :multiselect_options="this.dropdown_data1"
        :multi_select="true"
        :filter_select="true"
        :placeholder_value="'Language'"
        :labelanimation="true"
        @customChange="selectValue"
      ></hlxselect>
    </div>
    <div class="example-footer">
      <span
        class="icon"
        id="basic-multiselect-filter-icon"
        @click="showCode('basic-multiselect-filter')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="basic-multiselect-filter" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="basic_multiselect_filter"
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

  <h1 class="component-heading">Select with inline search</h1>
  <p class="component-description">
     To enable inline search in select set <b>:inline_search</b> to <b>true</b> 
  </p>
   <div class="component-example">
    <div class="example-body">
            <hlxselect
        :options="this.dropdown_data1"
        :placeholder_value="'Language'"
        :labelanimation="true"
        :inline_search="true"
        :prevalue="this.prevalue"
        @searchvalue="setvalue"
        @customChange="setvalue"
        @selectedvalue="setvalue1"
          ></hlxselect>
    </div>
    <div class="example-footer">
      <span
        class="icon"
        id="inline-search-icon"
        @click="showCode('inline-search')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
    <div class="source-code" id="inline-search" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="inline_search"
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
  <!-- <hlx-table-component :tableData="this.data.table_data" :theader="this.data.columns" :border="true"/> -->
    <h2 class="component-side-heading">Select attributes</h2>
  <!-- <hlx-table
    :data="this.table_data"
    :border="true"
    theme="secondary"
    :rowHover="true"
    :ellipses="5"
    :bold_header="true"
  >
    <hlx-column :prop="'attribute'" :label="'Name'" :type="'string'" />
    <hlx-column :prop="'description'" :label="'Description'" :type="'string'" />
    <hlx-column :prop="'default'" :label="'Default'" :type="'string'" />
    <hlx-column :prop="'type'" :label="'Type'" :type="'string'" :width="200" />
    <hlx-column
      :prop="'accepted_values'"
      :label="'Accepted values'"
      :type="'string'"
    />
    <hlx-column :prop="'mandatory'" :label="'Mandatory'" :type="'string'" />
  </hlx-table>

  <h2 class="component-side-heading">Events</h2>

  <hlx-table
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
      
      <h2 class="component-side-heading">Events</h2>
      
      <hlx-table-v2
    :border="['table', 'header', 'vertical', 'horizontal']"
    :boldHeaders="false"
    :rowHover="false"
    theme="primary"
    :stripedRows="false"
  >
  <h2 class="component-side-heading">Events</h2>
    <template #thead>
      <hlx-table-head v-for="(i, index) in this.selectevents" :key="index">{{
        i.label
      }}</hlx-table-head>
    </template>
    <template #tbody>
      <tr v-for="(i, index) in this.select_events" :key="index" id="">
        <hlx-table-cell
          v-for="(j, col_index) in this.selectevents"
          :align="'left'"
          :key="col_index"
        >
          {{ i[j.prop] }}
        </hlx-table-cell>
      </tr>
    </template>
  </hlx-table-v2>
</template>

<script>
// import hlxTable from "../components/NewTable.vue";
// import hlxColumn from "../components/NewTableColumn.vue";
import hlxTableV2 from "../components/table-v2/HlxTableV2.vue";
import hlxTableHead from "../components/table-v2/HlxTableHead.vue";
import hlxTableCell from "../components/table-v2/HlxTableCell.vue";
import divider from "../components/DividerComponent.vue";
import hlxselect from "../components/SelectComponent.vue";
import CodeEditor from "simple-code-editor";


export default {
  name: "App",
  components: {
    hlxselect,
    divider,
    CodeEditor,
    // hlxTable,
    // hlxColumn,
    hlxTableCell,
    hlxTableHead,
    hlxTableV2,
  },
  data() {
    return {
      data:{key:''},
      prevalue:'Php',
      check:[],
      value12:'',
      selectvalue:'',
      alertAttributes: [
        {
          prop: "attribute",
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
          prop: "type",
          label: "Type",
          width: "50",
          type: "string",
          format: "",
        },
        {
          prop: "accepted_values",
          label: "Accepted values",
          width: "50",
          type: "string",
          format: "",
        },
        {
          prop: "default",
          label: "Default",
          width: "50",
          type: "string",
          format: "",
        },
        {
          prop: "mandatory",
          label: "Mandatory",
          width: "50",
          type: "string",
          format: "",
        },
      ],
      selectevents:[
          {
          prop: "name",
          label: "Name",
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
      select_events:[  {
          name: "customChange",
          description: "Return the selected values from dropdown",
          parameters: "-",
        },
        {
           name: "searchvalue",
          description: "Emits the name of the newly added option",
          parameters: "-",
        },
        {
           name: "selectedvalue",
          description: "Emits the selected value",
          parameters: "-",
        }],
      pre_value: [
        {
          id: 7,
          name: "Stuart",
        },
      ],
      new_data: [
        {
          id: 1,
          flag: "in",
          name: "India",
          code: "+91",
          checked: false,
        },
        {
          id: 2,
          flag: "ca",
          name: "Canada",
          code: "+1",
          checked: false,
        },
        {
          id: 3,
          flag: "us",
          name: "USA",
          code: "+1",
          checked: false,
        },
      ],

      table_data: [
        {
          attribute: "options",
          description:
            "Pass the list of items to be added in the dropdown list",
          type: "String",
          accepted_values: "Array of objects",
          default: "-",
          mandatory: true,
        },
        {
          attribute: "dropdown_data",
          description:
            "Pass the list of items to be added in the dropdown list",
          type: "String",
          accepted_values: "Array of objects",
          default: "-",
          mandatory: true,
        },
        {
          attribute: "title",
          description: "Pass the title",
          type: "String",
          accepted_values: "enter the title",
          default: "-",
          mandatory: false,
        },
        {
          attribute: "placeholder",
          description: "Pass the placeholder",
          type: "String",
          accepted_values: "enter the placeholder",
          default: "-",
          mandatory: false,
        },
        {
          attribute: "multi_select",
          description:
            "boolean value which specifies whether to enable muli select or not",
          type: "Boolean",
          accepted_values: "true/false",
          default: "-",
          mandatory: true,
        },
      ],
      editor_theme: "light",
      inline_search:`
<template>
        <hlx-select
        :options="this.dropdown_data1"
        :placeholder_value="'Language'"
        :labelanimation="true"
        :inline_search="true"
          ></hlx-select>
</template>
<script> 
    export default {
    data() {
      return{
        dropdown_data1: [
            { name: "Php", checked: false, disabled: false, value: "Php",icon:'icon-database-regular',id:1},
            { name: "VueJs", checked: false, disabled: false, value: "VueJs" ,icon:'icon-database-regular',id:2},
            { name: "ReactJs", checked: false, disabled: false, value: "ReactJs" ,icon:'icon-database-regular',id:3 },
            { name: "Html", checked: false, disabled: false, value: "Html" ,icon:'icon-database-regular' ,id:4},
            { name: "Css", checked: false, disabled: false, value: "Css" ,icon:'icon-database-regular' ,id:5},
            { name: "Scss", checked: false, disabled: false, value: "Scss" ,icon:'icon-database-regular' ,id:6},
            { name: "Sass", checked: false, disabled: false, value: "Sass" ,icon:'icon-database-regular' ,id:7},
            { name: "Sql", checked: false, disabled: false, value: "Sql" ,icon:'icon-database-regular',id:8 },
            { name: "MongoDB", checked: false, disabled: false, value: "MongoDB" ,icon:'icon-database-regular',id:9},
            { name: "Javascript", checked: false, disabled: false, value: "Javascriptq" ,icon:'icon-database-regular' ,id:10},
          ],
      }
    }
    }
      `,
      basic_country_select:`
           <template>
                  <hlx-select
                  :options="this.new_data"
                  :placeholder_value="'CountryFlag'"
                  :labelanimation="true"
                  :icon="true"
                  @customChange="selectValue"
                ></hlx-select>
                </template>
                <script> 
                export default {
                      data() {
                  return{
                    new_data: [
                    {
                      id: 1,
                      flag: "in",
                      name: "India",
                      code: "+91",
                      checked: false,
                    },
                    {
                      id: 2,
                      flag: "ca",
                      name: "Canada",
                      code: "+1",
                      checked: false,
                    },
                    {
                      id: 3,
                      flag: "us",
                      name: "USA",
                      code: "+1",
                      checked: false,
                    },
                  ],
                  }
                }
                }
      `,
            basic_select: `
                <template>
                <hlx-select
                :options="this.dropdown_data"
                :placeholder_value="'Language'"
                :labelanimation="true"
                :clearable="true"
                v-model:value="this.selectvalue"
                @customChange="selectValue"
              ></hlx-select>
                </template>
                <script> 
                export default {
                                   data() {
                  return{
                      dropdown_data: [
                        { name: "Php", checked: false, disabled: false, value: "Php"},
                        { name: "VueJs", checked: false, disabled: false, value: "VueJs"  },
                        { name: "ReactJs", checked: false, disabled: false, value: "ReactJs"  },
                        { name: "Html", checked: false, disabled: false, value: "Html"  },
                        { name: "Css", checked: false, disabled: false, value: "Css"  },
                        { name: "Scss", checked: false, disabled: false, value: "Scss"  },
                        { name: "Sass", checked: false, disabled: false, value: "Sass"  },
                        { name: "Sql", checked: false, disabled: false, value: "Sql"  },
                        { name: "MongoDB", checked: false, disabled: false, value: "MongoDB" },
                        { name: "Javascript", checked: false, disabled: false, value: "Javascriptq"  },
                      ],
                  }
                }
                }
      `,
      basic_multiselect_filter:`
      <template>
            <hlx-select
              :multiselect_options="this.dropdown_data"
              :multi_select="true"
              :placeholder_value="'Language'"
              :labelanimation="true"
              @customChange="selectValue"
            ></hlx-select>
            </template>

            <script> 
                export default
                {
                data() {
                  return{
                        dropdown_data: [
                          { name: "Php", checked: false, disabled: false, value: "Php"},
                          { name: "VueJs", checked: false, disabled: false, value: "VueJs"  },
                          { name: "ReactJs", checked: false, disabled: false, value: "ReactJs"  },
                          { name: "Html", checked: false, disabled: false, value: "Html"  },
                          { name: "Css", checked: false, disabled: false, value: "Css"  },
                          { name: "Scss", checked: false, disabled: false, value: "Scss"  },
                          { name: "Sass", checked: false, disabled: false, value: "Sass"  },
                          { name: "Sql", checked: false, disabled: false, value: "Sql"  },
                          { name: "MongoDB", checked: false, disabled: false, value: "MongoDB" },
                          { name: "Javascript", checked: false, disabled: false, value: "Javascriptq"  },
                        ],
                  }
                }
                }
`,
            basic_multiselect: `
            <template>
            <hlx-select
              :multiselect_options="this.dropdown_data"
              :multi_select="true"
              :placeholder_value="'Language'"
              :labelanimation="true"
              @customChange="selectValue"
            ></hlx-select>
            </template>

            <script> 
                export default
                {
                  data() {
                  return{
                      dropdown_data: [
                          { name: "Php", checked: false, disabled: false, value: "Php"},
                          { name: "VueJs", checked: false, disabled: false, value: "VueJs"  },
                          { name: "ReactJs", checked: false, disabled: false, value: "ReactJs"  },
                          { name: "Html", checked: false, disabled: false, value: "Html"  },
                          { name: "Css", checked: false, disabled: false, value: "Css"  },
                          { name: "Scss", checked: false, disabled: false, value: "Scss"  },
                          { name: "Sass", checked: false, disabled: false, value: "Sass"  },
                          { name: "Sql", checked: false, disabled: false, value: "Sql"  },
                          { name: "MongoDB", checked: false, disabled: false, value: "MongoDB" },
                          { name: "Javascript", checked: false, disabled: false, value: "Javascriptq"  },
                        ],
                  }
                }

                }
      `,
      dropdown_data1: [
        { name: "Php", checked: false, disabled: false },
        { name: "VueJs", checked: false, disabled: false },
        { name: "ReactJs", checked: false, disabled: false },
        { name: "Html", checked: false, disabled: false },
        { name: "Css", checked: false, disabled: false },
        { name: "Scss", checked: false, disabled: false },
        { name: "Sass", checked: false, disabled: false },
        { name: "Sql", checked: false, disabled: false },
        { name: "MongoDB", checked: false, disabled: false },
        { name: "Javascript", checked: false, disabled: false },
      ],
      title: "Name",
      placeholder: "Sortby",
      search1: "",
      singleselectvalue: [],
      dropdown_data: [
        { name: "Php", checked: false, disabled: false, value: "Php"},
        { name: "VueJs", checked: false, disabled: false, value: "VueJs"  },
        { name: "ReactJs", checked: false, disabled: false, value: "ReactJs"  },
        { name: "Html", checked: false, disabled: false, value: "Html"  },
        { name: "Css", checked: false, disabled: false, value: "Css"  },
        { name: "Scss", checked: false, disabled: false, value: "Scss"  },
        { name: "Sass", checked: false, disabled: false, value: "Sass"  },
        { name: "Sql", checked: false, disabled: false, value: "Sql"  },
        { name: "MongoDB", checked: false, disabled: false, value: "MongoDB" },
        { name: "Javascript", checked: false, disabled: false, value: "Javascriptq"  },
      ],
      dropdown_data1: [
        { name: "Php", checked: false, disabled: false, value: "Php",icon:'icon-database-regular'},
        { name: "VueJs", checked: false, disabled: false, value: "VueJs" ,icon:'icon-database-regular' },
        { name: "ReactJs", checked: false, disabled: false, value: "ReactJs" ,icon:'icon-database-regular' },
        { name: "Html", checked: false, disabled: false, value: "Html" ,icon:'icon-database-regular' },
        { name: "Css", checked: false, disabled: false, value: "Css" ,icon:'icon-database-regular' },
        { name: "Scss", checked: false, disabled: false, value: "Scss" ,icon:'icon-database-regular' },
        { name: "Sass", checked: false, disabled: false, value: "Sass" ,icon:'icon-database-regular' },
        { name: "Sql", checked: false, disabled: false, value: "Sql" ,icon:'icon-database-regular' },
        { name: "MongoDB", checked: false, disabled: false, value: "MongoDB" ,icon:'icon-database-regular'},
        { name: "Javascript", checked: false, disabled: false, value: "Javascriptq" ,icon:'icon-database-regular' },
      ],
    };
  },
  mounted()
  {
      // console.log(this.selectvalue);
      // console.log(this.check);
  },
  methods: {
    showCode(val) {
      document.getElementById(val + "-icon").classList.toggle("active-icon");
      if (document.getElementById(val).style.display === "none") {
        document.getElementById(val).style.display = "block";
      } else if (document.getElementById(val).style.display === "block") {
        document.getElementById(val).style.display = "none";
      }
    },
    selectValue(value1) {
      this.singleselectvalue = value1;
      console.log('pop',this.check);
      console.log(this.singleselectvalue, "check");
      console.log(this.selectvalue);
    },
    setvalue(data1)
    {
        console.log(data1,'dataa');
    },
    setvalue1(data1)
    {
        console.log(data1,'datdlaa');
    },
    clear(value1) {
      let clearvalue = value1;
      console.log(clearvalue);
    },
  },
};
</script>

<style lang="scss" scoped>
.example-body {
  overflow: visible !important;
}
</style>