<template>
<h1 class="component-heading">Draggables</h1>
  <p class="component-description">
Draggable component allows drag-and-drop and synchronization with the reordering of associated array elements.  </p>
  <hlx-divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Basic usage</h2>
  <p class="component-description">Hold and drag to arrange the list</p>
  <p class="component-description">Whenever an item is re arranged, the new re arranged array is emitted as a v-model value
    <br>
    Pass the list of options as an array of object to the <b>:list</b> attribute.
  </p>
  <div class="component-example">
    <div class="example-body3">
        <hlx-draggables :list="this.list" v-model:value="this.listValue" />
    </div>
    <div class="example-footer">
        <!-- Replace your id wherever required -->
      <span class="icon" id="basic-draggables-icon" @click="showCode('basic-draggables')"><i class="icon-code-regular"></i></span>
    </div>
  </div>
  <div class="source-code" id="basic-draggables" style="display: none">
    <section class="example-source-wrapper">
        <div class="source">
          <CodeEditor
             :id="'editor'"  :display_language="false"
            :value="basic_draggables"
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
  <hlx-divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Selectable</h2>
  <p class="component-description">Use check boxes to select items, and re arrange them</p>
  <p class="component-description">Bind <b>:selectable="true"</b> to add checkboxes</p>
  <span class="component-description"> Each object must contain the following attributes to function properly : <br>
    <li class="component-description">name: (String) label name for each checkbox</li>
    <li class="component-description">checked: (true / false) sets whether the option must be pre-selected or not</li>
    <li class="component-description">disabled: (true / false) sets whether the option must be disabled or not</li>
    <li class="component-description">id: (unique id) distinguishes fields from each other</li>
    <br>
    </span>
  <div class="component-example">
    <div class="example-body3">
        <hlx-draggables :list="this.list2" :selectable="true" v-model:value="this.listValue"/>
        <!-- <hlx-draggables :list="this.list3" :selectable="true" v-model:value="this.listValue"/> -->
    </div>
    <div class="example-footer">
        <!-- Replace your id wherever required -->
      <span class="icon" id="selectable-draggables-icon" @click="showCode('selectable-draggables')"><i class="icon-code-regular"></i></span>
    </div>
  </div>
  <div class="source-code" id="selectable-draggables" style="display: none">
    <section class="example-source-wrapper">
        <div class="source">
          <CodeEditor
             :id="'editor'"  :display_language="false"
            :value="selectable_draggables"
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
  <hlx-divider :position="'horizontal'" :space="'20px'" />
  <h2 class="component-side-heading">Attributes</h2>
  <hlx-table
    :data="this.table_data"
    :border="true"
    theme="secondary"
    :rowHover="true"
    :ellipses="5"
    :bold_header="true"
  >
    <hlx-column :prop="'name'" :label="'Name'" :type="'string'" />
    <hlx-column :prop="'description'" :label="'Description'" :type="'string'" />
    <hlx-column :prop="'default'" :label="'Default'" :type="'string'" />
    <hlx-column :prop="'type'" :label="'Type'" :type="'string'" :width="200"/>
    <hlx-column :prop="'accepted_values'" :label="'Accepted values'" :type="'string'"/>
    <hlx-column :prop="'mandatory'" :label="'Mandatory'" :type="'string'" />
  </hlx-table>
</template>

<script>
import HlxDraggables from '../components/DraggableComponent.vue'
import HlxDivider from '../components/DividerComponent.vue'
import CodeEditor from 'simple-code-editor'
import HlxTable from '../components/NewTable.vue'
import HlxColumn from '../components/NewTableColumn.vue'

export default {
  components: {
    HlxDraggables,
    HlxDivider,
    CodeEditor,
    HlxTable,
    HlxColumn
  },
  data () {
    return {
      example_code: '``',
      editor_theme: 'light',
      listValue: [],
      list: [
        { name: 'Rachel', id: 1 },
        { name: 'Ross', id: 2 },
        { name: 'Chandler', id: 3 },
        { name: 'Monica', id: 4 }
      ],
      list2: [
        { name: 'Rachel', id: 1, checked: true, disabled: false },
        { name: 'Ross', id: 2, checked: true, disabled: false },
        { name: 'Chandler', id: 3, checked: true, disabled: false },
        { name: 'Monica', id: 4, checked: true, disabled: false }
      ],
      list3: [
        { name: 'Rachel', id: 1, checked: true, disabled: false },
        { name: 'Ross', id: 2, checked: true, disabled: false },
        { name: 'Chandler', id: 3, checked: false, disabled: false },
        { name: 'Monica', id: 4, checked: true, disabled: false }
      ],
      DraggablesAttributes: {
        columns: [
          {
            name: 'attribute',
            label: 'Attributes',
            width: '50',
            type: 'string',
            format: ''
          },
          {
            name: 'description',
            label: 'Description',
            width: '50',
            type: 'string',
            format: ''
          },
          {
            name: 'type',
            label: 'Type',
            width: '50',
            type: 'string',
            format: ''
          },
          {
            name: 'accepted_values',
            label: 'Accepted values',
            width: '50',
            type: 'string',
            format: ''
          },
          {
            name: 'default',
            label: 'Default',
            width: '50',
            type: 'string',
            format: ''
          },
          {
            name: 'mandatory',
            label: 'Mandatory',
            width: '50',
            type: 'string',
            format: ''
          }
        ],
        table_data: [{
          attribute: 'list',
          description:
            'pass the list of items to the draggable component',
          type: 'Array',
          accepted_values:
            'Array',
          default: '-',
          mandatory: true
        },
        {
          attribute: 'selectable',
          description:
            'adds check boxes to select the items from the array',
          type: 'Boolean',
          accepted_values:
            'true / false',
          default: 'false',
          mandatory: false
        }]
      },
      table_data: [{
        name: 'list',
        description:
            'Pass the list of items to the draggable component',
        type: 'Array',
        accepted_values:
            'Array',
        default: '-',
        mandatory: true
      },
      {
        name: 'selectable',
        description:
            'Adds check boxes to select the items from the array',
        type: 'Boolean',
        accepted_values:
            'true / false',
        default: 'false',
        mandatory: false
      }],
      basic_draggables: `
<template>
  <hlx-draggables :list="this.list" v-model:value="this.listValue" />
</template>

<script>
export default {
  data () {
    return {
      list: [
        { name: 'Rachel', id: 1 },
        { name: 'Ross', id: 2 },
        { name: 'Chandler', id: 3 },
        { name: 'Monica', id: 4 }
      ],
      listValue: []
    }
  }
}
</\script>
      `,
      selectable_draggables: `
<template>
  <hlx-draggables :list="this.list2" :selectable="true" v-model:value="this.listValue"/>
</template>

<script>
export default {
  data () {
    return {
      list2: [
        { name: 'Rachel', id: 1, checked: true, disabled: false },
        { name: 'Ross', id: 2, checked: true, disabled: false },
        { name: 'Chandler', id: 3, checked: true, disabled: false },
        { name: 'Monica', id: 4, checked: true, disabled: false }
      ],
      listValue: []
    }
  }
}
</\script>
      `
    }
  },
  methods: {
    log () {
      // console.log(this.listValue, 'emit list')
    },
    showCode (val) {
      document.getElementById(val + '-icon').classList.toggle('active-icon')
      if (document.getElementById(val).style.display === 'none') {
        document.getElementById(val).style.display = 'block'
      } else if (document.getElementById(val).style.display === 'block') {
        document.getElementById(val).style.display = 'none'
      }
    }
  }
}
</script>

<style>

</style>
