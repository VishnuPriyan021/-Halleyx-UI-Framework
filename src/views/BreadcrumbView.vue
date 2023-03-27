<template>
  <h1 class="component-heading">Breadcrumb</h1>
  <p class="component-description">
    Indicate the current page’s location within a navigational hierarchy that
    adds separators.
  </p>
  <divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Basic usage</h2>
  <p class="component-description">
    To specify the array for <b>:items</b>.
    This will push value to params and you can route to your specific page using
    routers
  </p>
   <div class="notes">
    <p class="note-title" >Note:</p><p class="note-body"> Default separator set as <i> '/' </i></p>
  </div>
  <div class="component-example">
    <div class="example-body">
       <span class="breadcrumb-area">
      <hlx-breadcrumb :items="items" @path="pathTo" />
       </span>
    </div>
    <div class="example-footer">
      <span class="icon" id="breadcrumb-icon" @click="showCode('breadcrumb')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="breadcrumb" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="bredcrumb_source"
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
  <h2 class="component-side-heading">Custom separator</h2>
   <p class="component-description">
    To specify the <b>:separator</b> as String or Object</p>
    <p class="component-description">For the special characters <b>:separator="'>'"</b> directly add as string, for custom icon <b>:separator="separator"</b> the separator value will be in Object type
    
  </p>
  <div class="component-example">
    <div class="example-body">
       <span class="breadcrumb-area">
      <hlx-breadcrumb :items="items" :separator="separator" @path="pathTo"/>
       </span>
    </div>
    <div class="example-footer">
      <span class="icon" id="breadcrumb1-icon" @click="showCode('breadcrumb1')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="breadcrumb1" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="bredcrumb_source1"
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
  <h2 class="component-side-heading">Attributes</h2>

  <hlx-table
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

  <divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Events</h2>
  <hlx-table
    :data="this.table_data1"
    :border="true"
    theme="secondary"
    :rowHover="true"
    :ellipses="5"
    :bold_header="true"
  >
    <hlx-column :prop="'Name'" :label="'Name'" :type="'string'" />
    <hlx-column :prop="'Description'" :label="'Description'" :type="'string'" />
    <hlx-column :prop="'Parameters'" :label="'Default'" :type="'string'" />
  </hlx-table>
</template>

<script>
import hlxBreadcrumb from "../components/BreadcrumbComponent.vue";
import CodeEditor from "simple-code-editor";
import divider from "../components/DividerComponent.vue";
import hlxTable from "../components/NewTable.vue";
import hlxColumn from "../components/NewTableColumn.vue";
export default {
  name: "App",
  components: {
    hlxBreadcrumb,
    CodeEditor,
    divider,
    hlxTable,
    hlxColumn,
  },
  data() {
    return {
      items: [
        { label: 'Home', link: '/' ,icon:'icon-home-regular'},
        { label: 'Category', link: '/breadcrumb' },
        { label: 'Product', link: '/braedcrumb/product' }
      ],
      separator:{icon:'icon-angles-right-small-filled'},
      editor_theme: "light",
      direction: "vertical",
      bredcrumb_source: `<template>
      <hlx-breadcrumb :items="items" @path="pathTo" />
<template>
<script>
   export default {
    data ()
    {
      return{
        items: [
       { label: 'Home', link: '/' ,icon:'icon-home-ot'},
        { label: 'Category', link: '/breadcrumb' },
        { label: 'Product', link: '/braedcrumb/product' }
      ],
      ]
      }
    }
   }
`,
      bredcrumb_source1: `<template>
      <hlx-breadcrumb :items="items" :separator="separator" @path="pathTo"/>
<template>
<script>
   export default {
    data ()
    {
      return{
        items: [
        { label: 'Home', link: '/' ,icon:'icon-home-ot'},
        { label: 'Category', link: '/breadcrumb' },
        { label: 'Product', link: '/braedcrumb/product' }
      ],
      separator:{icon:'icon-arrow-right-ot'},
      }
    },
    methods:{
      pathTo(val) {
      console.log("val",val);
      this.$router.push(val.link)
    }
    }
   }`,

      table_data: [
        {
          attribute: "separator",
          description: "Specify the separator between list",
          type: "symbols",
          accepted_values: "[>,/,-,>>]",
          default: "/",
          mandatory: false,
        },
        {
          attribute: "items",
          description: "Specify the array",
          type: "Array",
          accepted_values: "array of values",
          default: "-",
          mandatory: true,
        },
      ],
      table_data1: [
         {
           Name:'path',
           Description:'Emits the option chosen',
           Parameters:'-'
         },
      ],
        
    };
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
    pathTo(val) {
      console.log("val",val);
      this.$router.push(val.link)
    },
  },
};
</script>