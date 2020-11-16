<template>
  <div class="ui vertical segment">
    <div class="flexbox">
      <div class="flex-content">
        <div class="button-group">
          <button type="button" @click="reset" class="small ui button">reset</button>
          <button type="button" @click="selectItem" class="small ui button">select from parent</button>
        </div>
        <div>
          <list-select
            :list="someList"
            option-value="code"
            option-text="html"
            :selected-item="item"
            id="mySelectId"
            name="mySelectName"
            placeholder="select item"
            @select="onSelect"
          >
          </list-select>
        </div>
      </div>
      <div class="flex-result">
        <table class="ui celled table">
          <thead>
          <tr>
            <th>code</th>
            <th>name</th>
            <th>desc</th>
          </tr>
          </thead>
          <tbody>
          <tr>
            <td>{{item.code}}</td>
            <td>{{item.name}}</td>
            <td>{{item.desc}}</td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import { ListSelect } from '../lib'

export default {
  data () {
    return {
      someList: [
        { code: '01', name: 'aa', desc: 'desc01', html: '<strong>test</strong>' },
        { code: '02', name: 'ab', desc: 'desc02', html: '<strong>test 2</strong>' },
        { code: '03', name: 'bc', desc: 'desc03', html: '<strong>test 3</strong>' },
        { code: '04', name: 'cd', desc: 'desc04', html: '<strong>test 4</strong>' },
        { code: '05', name: 'de', desc: 'desc05', html: '<strong>test 5</strong>' },
        { code: '06', name: 'ef', desc: 'desc06', html: '<strong>test 6</strong>' }
      ],
      item: {
        code: '',
        name: '',
        desc: ''
      }
    }
  },
  methods: {
    onSelect (item) {
      this.item = item
    },
    reset () {
      this.item = {}
    },
    selectItem () {
      // select option from parent component
      this.item = this.someList[0]
    }
  },
  components: {
    ListSelect
  }
}
</script>
