<template>
  <div class="md-example-child md-example-child-dialog md-example-child-dialog-0">
    <md-button @click="basicDialog.open = true">基本</md-button>
    <md-button @click="iconDialog.open = true">带图标</md-button>
    <md-button @click="warnDialog.open = true">警示操作</md-button>
    <md-button @click="actDialog.open = true">多操作</md-button>

    <md-dialog
      title="窗口标题"
      :closable="true"
      v-model="basicDialog.open"
      :btns="basicDialog.btns"
    >
      人生的刺，就在这里，留恋着不肯快走的，偏是你所不留恋的东西。
    </md-dialog>

    <md-dialog
      icon="location"
      :closable="true"
      v-model="iconDialog.open"
      :btns="iconDialog.btns"
    >
      围在城里的人想逃出来，城外的人想冲进去，对婚姻也罢，职业也罢，人生的愿望大都如此。
    </md-dialog>

    <md-dialog
      title="警示操作"
      :closable="false"
      v-model="warnDialog.open"
      :btns="warnDialog.btns"
    >
      或是因为习惯了孤独，我们渴望被爱；又或是害怕爱而不得，我们最后仍然选择孤独。
    </md-dialog>

    <md-dialog
      title="窗口标题"
      :closable="false"
      layout="column"
      v-model="actDialog.open"
      :btns="actDialog.btns"
    >
      据说每个人需要一面镜子，可以常常自照，知道自己是个什么东西。不过，能自知的人根本不用照镜子；不自知的东西，照了镜子也没有用。
    </md-dialog>
  </div>
</template>

<script>import {Dialog, Button, Toast} from 'mand-mobile'

export default {
  name: 'dialog-demo',
  components: {
    [Dialog.name]: Dialog,
    [Button.name]: Button,
  },
  data() {
    return {
      basicDialog: {
        open: false,
        btns: [
          {
            text: '取消',
            handler: this.onBasicCancel,
          },
          {
            text: '确认操作',
            handler: this.onBasicConfirm,
          },
        ],
      },
      iconDialog: {
        open: false,
        btns: [
          {
            text: '确认操作',
            handler: this.onIconConfirm,
          },
        ],
      },
      warnDialog: {
        open: false,
        btns: [
          {
            text: '取消',
          },
          {
            text: '警示操作',
            warning: true,
          },
        ],
      },
      actDialog: {
        open: false,
        btns: [
          {
            text: '操作一',
            type: 'danger',
            handler: this.onActConfirm,
          },
          {
            text: '操作二',
            handler: this.onActConfirm,
          },
          {
            text: '操作三',
            handler: this.onActConfirm,
          },
        ],
      },
    }
  },
  methods: {
    onBasicConfirm() {
      Toast({
        content: '你点击了确认',
      })
      this.basicDialog.open = false
    },
    onBasicCancel() {
      Toast({
        content: '你点击了取消',
      })
      this.basicDialog.open = false
    },
    onIconConfirm() {
      Toast({
        content: '你点击了确认',
      })
      this.iconDialog.open = false
    },
    onActConfirm() {
      this.actDialog.open = false
    },
  },
}
</script>
