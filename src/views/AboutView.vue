<template>
  <div>
    <h3>
      欢迎来到你的个人图片站！
      下面开始浏览吧~
    </h3>
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
  <el-button slot="trigger" size="small" type="primary">选择图片</el-button>
  <el-button style="margin-left: 10px;" size="small" type="success" @click="uploadForm">上传到服务器</el-button>
  <div class="el-upload__tip" slot="tip">请上传图片文件</div>
</el-upload>
    <viewer>
    <!-- <img v-for="src in descImgs " :src="src" :key="src" style="width: 200px;height: 200px"> -->
    <img v-for="(decImg, index) in descImgs" :key="index" :src="decImg" style="width: 200px;height: 200px">
  </viewer>
  </div>
</template>

<script>
export default {
  data () {
    return {
      descImgs: [ 'https://fuss10.elemecdn.com/1/34/19aa98b1fcb2781c4fba33d850549jpeg.jpeg',
        'https://fuss10.elemecdn.com/1/34/19aa98b1fcb2781c4fba33d850549jpeg.jpeg',
        'https://fuss10.elemecdn.com/0/6f/e35ff375812e6b0020b6b4e8f9583jpeg.jpeg',
        'https://fuss10.elemecdn.com/9/bb/e27858e973f5d7d3904835f46abbdjpeg.jpeg', 
        'https://fuss10.elemecdn.com/d/e6/c4d93a3805b3ce3f323f7974e6f78jpeg.jpeg',
        'https://fuss10.elemecdn.com/3/28/bbf893f792f03a54408b3b7a7ebf0jpeg.jpeg',
        'https://fuss10.elemecdn.com/2/11/6535bcfb26e4c79b48ddde44f4b6fjpeg.jpeg',
        'https://fuss10.elemecdn.com/1/34/19aa98b1fcb2781c4fba33d850549jpeg.jpeg',
        'https://fuss10.elemecdn.com/0/6f/e35ff375812e6b0020b6b4e8f9583jpeg.jpeg',
        'https://fuss10.elemecdn.com/9/bb/e27858e973f5d7d3904835f46abbdjpeg.jpeg', 
        'https://fuss10.elemecdn.com/d/e6/c4d93a3805b3ce3f323f7974e6f78jpeg.jpeg',
        'https://fuss10.elemecdn.com/3/28/bbf893f792f03a54408b3b7a7ebf0jpeg.jpeg',
        'https://fuss10.elemecdn.com/2/11/6535bcfb26e4c79b48ddde44f4b6fjpeg.jpeg'
      ]
    }
  }
}
</script>
