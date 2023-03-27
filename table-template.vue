<template>
Below is a template for adding documentation with table component....Replace your component name and data accordingly..
---------------------------------------------------------------------------------------------------------------------
<h2> `your component name` Attributes</h2>
<!-- replace your table data below -->
 <hlx-table
 :data="this.attributes_data"
 :border="true"
 theme="secondary"
 :rowHover="true"
 :bold_header="true"
 >
 <hlx-column
  :prop="'name'"
  :label="'Name'"
  :type="'string'"
 />
 <hlx-column
  :prop="'description'"
  :label="'Description'"
  :type="'string'"
 />
 <hlx-column
  :prop="'default'"
  :label="'Default'"
  :type="'string'"
 />
 <hlx-column
  :prop="'type'"
  :label="'Type'"
  :type="'string'"
 />
 <hlx-column
  :prop="'accepted_values'"
  :label="'Accepted values'"
  :type="'string'"
 />
 <hlx-column
  :prop="'mandatory'"
  :label="'Mandatory'"
  :type="'string'"
 />
 </hlx-table>
 <br>
 <br>

<h2>`your component name` Events</h2>
<!-- replace your table data below -->
 <hlx-table
 :data="this.events_data"
 :border="true"
 theme="secondary"
 :rowHover="true"
 :bold_header="true"
 >
 <hlx-column
  :prop="'name'"
  :label="'Name'"
  :type="'string'"
 />
 <hlx-column
  :prop="'description'"
  :label="'Description'"
  :type="'string'"
 />
 <hlx-column
  :prop="'parameters'"
  :label="'Parameters'"
  :type="'string'"
 />
 </hlx-table>
</template>

<script>
export default {
  data () {
    return {
      // Below is an example for attributes table data
      attributes_data: [
        {
          name: 'data',
          description: 'Table data',
          type: 'Array of objects',
          accepted_values: '-',
          mandatory: '-',
          default: '-'
        },
        {},
        {}
        // and so on...
      ],
      // Below is an example for events table data
      events_data: [
        {
          name: 'data',
          description: 'Table data',
          parameters: 'column, event'
        },
        {},
        {}
        // and so on...
      ]
    }
  }
}
</script>
