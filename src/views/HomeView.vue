<template>
  

  <div>
    <el-upload
  class="upload-demo"
  ref="upload"
  action=""
  :auto-upload="false"     
  multiple
  :file-list="fileList"  
  :limit="6"               
  list-type="picture"
  :on-preview="handlePreview"
  :on-remove="handleRemove"
          >
  <el-button slot="trigger" size="small" type="primary">select file</el-button>
  <el-button style="margin-left: 10px;" size="small" type="success" @click="uploadForm">upload to server</el-button>
  <div class="el-upload__tip" slot="tip">jpg/png files with a size less than 500kb</div>
</el-upload>


  </div>
</template>



<script>

  export default {
    name: 'HomeView',
    data() {
      return {
        fileList: [{name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {name: 'food2.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]
      };

    },
    methods: {
    uploadForm() {
      // this.$refs.upload.submit()
      if (this.fileList.length === 0) {
        this.$message.warning('请选取文件')
        return;
      }
      let formData = new FormData();
   // 因为要传一个文件数组过去，所以要循环append
   debugger
   this.$refs.fileList.forEach(file => {
        formData.append('file', file.raw)
      })
      // this.$refs.fileList.forEach(file => {
      //   formData.append('files', file.raw)
      // })


      // for(let i= 0;i<this.fileList.length;i++){
	    //   formData.append("files", this.fileList[i].raw);
      // }
      this.axios.post('http://127.0.0.01:3231/img/imgupload', formData,{
        headers: {
            'Content-Type': 'multipart/form-data'
          }
      }).then((resp)=>{
            console.log(resp);
            let data = resp.data;
            console.log(data);
            if(data.success){
              this.ruleForm= {};
                this.$message({
                message: '恭喜你,注册成功,点击去登陆按钮进行登陆吧!!!',
                type: 'success'
                });
            }
        })
      // this.$refs.upload.submit();
      // 清空图片列表（一定要清空，否则上传成功后还是会调用handleChange（）函数，上传成功后列表中还存在图片）
      this.fileList = []
    },
    handleRemove(file, fileList) {
        console.log(file, fileList);
      },
      handlePreview(file) {
        console.log(file);
      }
    }
  }
</script>