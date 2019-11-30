<template>
  <div class="home">this is 2-2 page</div>
</template>

<script>
// @ is an alias to /src
/**
 * axios请求方法： get post put patch delete
 * get 获取数据
 * post 提交数据（表单提交+文件上传）
 * put 更新数据（所有数据推送到后端）
 * patch 更新数据（只将修改的数据推送到后端）
 * delete 删除数据
 */
import axios from 'axios'

export default {
  name: 'axios2-2',
  components: {
  },
  created() {
    // localhost:8080访问的实际上是public下的index.html 所以接口直接/
    // axios get请求别名
    axios.get('/data.json', {
      params: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })
    // get
    axios({
      method: 'get',
      url: '/data.json',
      params: { id: 12 }
    }).then(res => {
      console.log(res)
    })

    // post请求别名方法  axios post方法
    /**
     * 请求数据格式两种
     * application/json
     * form-data 表单提交（图片、文件上产）
     */
    let data = {
      data: 12
    }
    // Content-Type: application/json;charset=UTF-8
    axios.post('/post', data).then(res => {
      console.log(res)
    })
    // 或
    axios({
      method: 'post',
      url: '/post',
      data: data
    }).then(res => {
      console.log(res)
    })

    // form-data请求  Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryrTgdWVbdHzYVJvPR
    let formData = new FormData()
    for(let key in data) {
      formData.append(key, data[key])
    }
    axios.post('/post',formData).then(res => {
      console.log(res)
    })

    // put请求和patch请求与post 类似

    // delete 参数在url后边
    axios.delete('/delete', {
      params: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })
    // 或者  参数在请求体
    axios.delete('/delete', {
      data: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })

  }
}
</script>
