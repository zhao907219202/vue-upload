<template>
  <div class="container-fluid" id="scriptTable">
    <h3>Land-Mine DWJ</h3>
    <form style="margin-top: 1rem">
      <input type="file" @change="getFile($event)" class="" multiple/>
      <input type="button" value="upload" @click="submit($event)" class="btn btn-dark">
    </form>
    <table class="table table-hover text-center table-bordered"
           style="word-break: break-all; word-wrap: break-word;margin-top: 1rem;">
      <thead>
      <th>#</th>
      <th>Platform</th>
      <th>Action</th>
      <th>Path</th>
      <th>Value</th>
      <th>Wait</th>
      <th>Screenshot</th>
      ßß
      <th>Change</th>
      </thead>
      <tbody>
      <tr v-cloak v-for="(item, index) in steps" :key="item">
        <th>{{index+1}}</th>
        ßß
        <td>{{item.platform}}</td>
        <td>{{item.action}}</td>
        <td>{{item.path}}</td>
        <td>{{item.value}}</td>
        <td>{{item.wait}}</td>
        <td>{{item.screenshot}}</td>
        <td><a href="#" v-on:click="edit(item)">Edit</a> | <a href="#" v-on:click='aaa(index)'>Delete</a>
        </td>
      </tr>
      <tr>
        <th></th>
        <td><select class="form-control" v-model="stepstemp.platform">
          <option>Web</option>
          <option>Android</option>
        </select></td>
        <td><select class="form-control" v-model="stepstemp.action">
          <option>click</option>
          <option>get</option>
          <option>input</option>
          <option>swipe</option>
        </select></td>
        <td><input class="form-control" v-model="stepstemp.path" placeholder="Enter the xPath"></td>
        <td><input class="form-control" v-model="stepstemp.value" placeholder="Enter the input value"></td>
        <td><input class="form-control" v-model="stepstemp.wait" placeholder="Waiting seconds"></td>
        <td><select class="form-control" v-model="stepstemp.screenshot">
          <option>yes</option>
          <option>no</option>
        </select></td>
        <td>
          <button class="btn btn-sm btn-dark" v-on:click='save' v-if="isNotEdit">Save</button>
          <button class="btn btn-sm btn-primary" v-on:click='saveEdit' v-else>SaveEdit</button>
        </td>
      </tr>
      </tbody>
    </table>
    <hr/>
  </div>
</template>

<script>
export default {
  name: 'ScriptTable',
  data () {
    return ({
      steps: [],
      stepstemp: {
        platform: '',
        action: '',
        path: '',
        value: '',
        wait: '',
        screenshot: ''
      },
      isNotEdit: true
    })
  },
  methods: {
    save: function () {
      this.steps.push(this.stepstemp)
      this.stepstemp = {
        platform: '',
        action: '',
        path: '',
        value: '',
        wait: '',
        screenshot: ''
      }
    },
    aaa: function (index) {
      this.steps.splice(index, 1)
    },
    edit: function (item) {
      this.isNotEdit = false
      this.stepstemp = item
    },
    saveEdit: function () {
      this.isNotEdit = true
      this.stepstemp = {
        platform: '',
        action: '',
        path: '',
        value: '',
        wait: '',
        screenshot: ''
      }
    }
  }
}
</script>

<style scoped>

</style>
