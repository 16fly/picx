<template>
  <div>
    <div class="tool-item">
      <el-switch
        v-model="setMaxSize"
        inactive-text="设置上传图片大小"
        @change="setMaxSizeChange"
        style="margin-right: 20px"
      >
      </el-switch>
      <el-input-number v-model="maxSize"
                       :disabled="!setMaxSize"
                       size="mini"
                       :min="100"
                       :max="1000"
                       :step="50"
                       @change="maxSizeChange"
                       label="图片大小"
      ></el-input-number>
    </div>
    <div class="tool-item">
      <el-switch
        v-model="rename"
        inactive-text="哈希命名"
        @change="renameChange"
      >
      </el-switch>
    </div>
    <div class="tool-item operation-btn">
      <el-button type="primary"
                 icon="el-icon-refresh"
                 @click="uploadReset"
      >重置
      </el-button>

      <el-button type="primary"
                 icon="el-icon-upload"
                 @click="uploadFile"
      >上传
      </el-button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "UploadTools",

    data() {
      return {
        setMaxSize: false,
        maxSize: 200,
        rename: true,
      }
    },

    mounted() {
      this.setMaxSizeChange(this.setMaxSize)
      this.maxSizeChange(this.maxSize)
      this.renameChange(this.rename)
    },


    methods: {
      setMaxSizeChange(e) {
        this.$emit('is-set-max-size', e)
      },

      renameChange(e) {
        this.$emit('is-rename', e)
      },

      maxSizeChange(e) {
        this.$emit('max-size', e)
      },

      uploadReset() {
        this.$emit('upload-reset')
      },

      uploadFile() {
        this.$emit('upload-file')
      }

    },

    props: {}
  }
</script>

<style scoped lang="scss">

  .tool-item {
    width: 100%;
    display: flex;
    align-items: center;
    margin-bottom: 10px;

    &:last-child {
      margin-bottom: 0;
    }
  }

  .operation-btn {
    justify-content: flex-end;
  }

</style>
