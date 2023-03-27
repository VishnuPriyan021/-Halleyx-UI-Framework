<template>
  <h1 class="component-heading">Dotted pagination</h1>
  <p class="component-description">
    The number of elements (images, articles, commentaries, pages, etc.) that
    can be loaded within a given context is communicated by pagination. It
    displays the user's current location and provides direct access to previous
    and subsequent content items.
  </p>
  <h2 class="component-side-heading">Basic usage</h2>
  <p class="component-description">
    Set <b> :dots</b> to specify how many dot needed on the pagination<br />
  </p>
  <!-- <h2 class="component-sidedot-heading">Basic usage</h2>
  <p class="component-description">Add the number of pager count in dot</p> -->
  <div class="component-example">
    <div class="example-body">
      <hlx-dotted-pagination
        :dots="5"
        @current-page="currentPage"
        @current-page-hover="currentPageHover"
      />
    </div>
    <div class="example-footer">
      <span
        class="icon"
        id="dotted-pagination-icon"
        @click="showCode('dotted-pagination')"
        ><i class="icon-code-regular"></i
      ></span>
    </div>
  </div>
  <div class="source-code" id="dotted-pagination" style="display: none">
    <section class="example-source-wrapper">
      <div class="source">
        <CodeEditor
          :id="'editor'"
          :display_language="false"
          :value="dotted_pagination"
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

  <h2 class="component-side-heading">Attributes</h2>
  <hlx-table-v2
    :border="['table', 'header', 'vertical', 'horizontal']"
    :boldHeaders="false"
    :rowHover="false"
    theme="primary"
    :stripedRows="false"
  >
    <template #thead>
      <hlx-table-head
        v-for="(i, index) in this.dottedAttributes"
        :key="index"
        >{{ i.label }}</hlx-table-head
      >
    </template>
    <template #tbody>
      <tr v-for="(i, index) in this.table_data" :key="index" id="">
        <hlx-table-cell
          v-for="(j, col_index) in this.dottedAttributes"
          :align="'left'"
          :key="col_index"
        >
          {{ i[j.prop] }}
        </hlx-table-cell>
      </tr>
    </template>
  </hlx-table-v2>

  <h2 class="component-side-heading">Events</h2>

  <!-- Events -->
  <hlx-table-v2
    :border="['table', 'header', 'vertical', 'horizontal']"
    :boldHeaders="false"
    :rowHover="false"
    theme="primary"
    :stripedRows="false"
  >
    <template #thead>
      <hlx-table-head v-for="(i, index) in this.dottedEvents" :key="index">{{
        i.label
      }}</hlx-table-head>
    </template>
    <template #tbody>
      <tr v-for="(i, index) in this.event_data" :key="index" id="">
        <hlx-table-cell
          v-for="(j, col_index) in this.dottedEvents"
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
import hlxDottedPagination from "../components/DottedPagination.vue";
import CodeEditor from "simple-code-editor";
import hlxTableV2 from "../components/table-v2/HlxTableV2.vue";
import hlxTableHead from "../components/table-v2/HlxTableHead.vue";
import hlxTableCell from "../components/table-v2/HlxTableCell.vue";
export default {
  name: "paginationView",
  components: {
    hlxDottedPagination,
    hlxTableCell,
    hlxTableHead,
    hlxTableV2,
    CodeEditor,
  },
  data() {
    return {
      editor_theme: "light",
      table_data: [
        {
          attribute: "dots",
          description: "To specify how many dot needed on the pagination",
          type: "Number",
          accepted_values: ">1",
          default: "-",
          mandatory: true,
        },
      ],
      dottedAttributes: [
        {
          prop: "attribute",
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
      dottedEvents: [
        {
          prop: "event_name",
          label: "Event name",
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
          prop: "parameter",
          label: "Parameter",
          width: "50",
          type: "string",
          format: "",
        },
      ],
      event_data: [
        {
          event_name: "current-page",
          description: "get current page on each click",
          parameter: "currentPage",
        },
      ],
      dotted_pagination: `
<template>
        <hlx-dotted-pagination :dots="5" @current-page="currentPage" @current-page-hover="currentPageHover" />
</template>

<script>
export default {
 methods: {
    currentPage(page){console.log(page)},
    currentPageHover(hoverd_page){console.log(hoverd_page)},
}
}
<\/script>


      `,
    };
  },
  methods: {
    currentPage(page) {
      console.log(page);
    },
    currentPageHover(hoverd_page) {
      console.log(hoverd_page);
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

<style lang="scss">
code {
  margin: 0;
  border-radius: 4px;
  padding: 0.15rem 0.5rem;
  font-size: 14px;
  color: black;
  line-height: 1.4;
  background-color: #f5f7fa;
}
</style>
