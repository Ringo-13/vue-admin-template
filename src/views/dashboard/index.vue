<template>
  <div class="dashboard-container">
    <p style="background-color:yellow;text-align:center;font-size:50px">
      欢迎
    </p>
    <p style="color:LightSlateGray;font-size:25px" >
    校园管理系统
    <br>
    网页实训项目
    <br>
    18应用3-1班 1803010127 林煜堃
    </p>
    <div class='item' style="width:130px;">
      <h1>学生总数</h1>
      <h1 style="text-align:center;">{{studentCount}}</h1>
	</div>
  <div class='item' style="width:130px;">
		<h1>班级总数</h1>
		<h1 style="text-align:center;">{{classsCount}}</h1>
	</div>
  <div class='item' style="width:130px;">
		<h1>老师总数</h1>
		<h1 style="text-align:center;">{{teacherCount}}</h1>
	</div>
  <div class='item' style="width:130px;">
		<h1>学院总数</h1>
		<h1 style="text-align:center;">{{academyCount}}</h1>
	</div>
  <div class='item' style="width:130px;">
		<h1>学校总数</h1>
		<h1 style="text-align:center;">{{schoolCount}}</h1>
	</div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  data() {
    return {
      students: '',
      studentCount: '',
      classs: '',
      classsCount: '',
      teacher: '',
      teacherCount: '',
      academy: '',
      academyCount: '',
      school: '',
      schoolCount: ''
    }
  },
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  mounted() {
    this.$http.post('/api/student/get').then(res => {
      this.students = res
      this.studentCount = this.students.length
      console.log(this.studentCount)
    })
    this.$http.post('/api/classs/get').then(res => {
      this.classs = res
      this.classsCount = this.classs.length
      console.log(this.classsCount)
    })

    this.$http.post('/api/teacher/get').then(res => {
      this.teacher = res
      this.teacherCount = this.teacher.length
      console.log(this.teacherCount)
    })

    this.$http.post('/api/academy/get').then(res => {
      this.academy = res
      this.academyCount = this.academy.length
      console.log(this.academyCount)
    })

    this.$http.post('/api/school/get').then(res => {
      this.school = res
      this.schoolCount = this.school.length
      console.log(this.schoolCount)
    })
  }
}
</script>

<style lang="scss" scoped>
  .dashboard {
    &-container {
      margin: 30px;
    }
    &-text {
      font-size: 30px;
      line-height: 46px;
    }
  }
</style>
