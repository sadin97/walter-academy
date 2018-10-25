<template>
  <div class="container">
    <el-row :gutter="20">

      <el-col :span="12" v-for="(course, i) in filteredData" :key="i">
        <el-card class="courseCard">
          <img :src="course.image" class="image">
          <div style="padding: 14px;">
            <span>{{course.title}}</span>
            <div class="bottom clearfix">
              <time class="time">{{course.date}}</time>
            </div>
          </div>
        </el-card>
      </el-col>

    </el-row>

    <el-row>
      <el-pagination
        background
        :data="courses"
        :page-size="1"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        layout="prev, pager, next"
        :total="numberOfPages">
      </el-pagination>
    </el-row>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        numberOfPages: null,
        filteredData: null,
        courses: [
          { id: 0, title: 'Revit Course 0', date: '20.01.2019.', image: 'https://walter.ba/cms/wp-content/uploads/Copy-of-Everyone-NeedsAdventure..png' },
          { id: 1, title: 'Revit Course 1', date: '20.01.2019.', image: 'https://walter.ba/cms/wp-content/uploads/Copy-of-Everyone-NeedsAdventure..png' },
          { id: 2, title: 'Revit Course 2', date: '20.01.2019.', image: 'https://images.pexels.com/photos/248797/pexels-photo-248797.jpeg?auto=compress&cs=tinysrgb&h=350' },
          { id: 3, title: 'Revit Course 3', date: '20.01.2019.', image: 'https://www.gettyimages.ca/gi-resources/images/Homepage/Hero/UK/CMS_Creative_164657191_Kingfisher.jpg' },
          { id: 4, title: 'Revit Course 4', date: '20.01.2019.', image: 'https://images.pexels.com/photos/34950/pexels-photo.jpg?auto=compress&cs=tinysrgb&h=350' },
          { id: 5, title: 'Revit Course 5', date: '20.01.2019.', image: 'https://www.w3schools.com/w3css/img_lights.jpg' },
          { id: 6, title: 'Revit Course', date: '20.01.2019.', image: 'https://cdn.pixabay.com/photo/2016/10/27/22/53/heart-1776746_960_720.jpg' },
          { id: 7, title: 'Revit Course', date: '20.01.2019.', image: 'https://wallpaperbrowse.com/media/images/3848765-wallpaper-images-download.jpg' },
          { id: 8, title: 'Revit Course', date: '20.01.2019.', image: 'https://cdn.vox-cdn.com/thumbor/lV5E8BPA4ej6sLO4Q92iAXjw-Ls=/0x0:1500x1000/1200x800/filters:focal(630x380:870x620)/cdn.vox-cdn.com/uploads/chorus_image/image/58769211/akrales_160708_1123_A_0039.0.0.jpg' },
          { id: 9, title: 'Revit Course', date: '20.01.2019.', image: 'https://i.dailymail.co.uk/i/pix/2016/09/06/11/37F60FD200000578-0-image-a-5_1473156426673.jpg' },
          { id: 10, title: 'Revit Course', date: '20.01.2019.', image: 'https://www.gettyimages.in/gi-resources/images/Homepage/Hero/US/SEP2016/prestige-476863311.jpg' },
          { id: 11, title: 'Revit Course', date: '20.01.2019.', image: 'https://www.w3schools.com/howto/img_forest.jpg' },
          { id: 12, title: 'Revit Course', date: '20.01.2019.', image: 'https://www.bmw.ie/content/dam/bmw/common/all-models/m-series/m4-convertible/2017/images-and-videos/images/BMW-m4-convertible-images-and-videos-1920x1200-06.jpg.asset.1487344406677.jpg' },
          { id: 13, title: 'Revit Course', date: '20.01.2019.', image: 'https://wallpaperbrowse.com/media/images/fall-autumn-red-season_WV7Vb7u.jpg' },
          { id: 14, title: 'Revit Course', date: '20.01.2019.', image: 'https://wallpaperbrowse.com/media/images/soap-bubble-1958650_960_720.jpg' },
          { id: 15, title: 'Revit Course', date: '20.01.2019.', image: 'https://cdn.pixabay.com/photo/2018/06/09/22/56/peacock-3465442_960_720.jpg' }
        ]
      }
    },
    created () {
      let brojPage = null
      if (this.courses.length % 6 > 0) {
        brojPage = (this.courses.length / 6) + 1
      } else {
        brojPage = (this.courses.length / 6)
      }
      this.numberOfPages = (Math.floor((brojPage)))
      console.log('numberOfPages: ', this.numberOfPages, ', duzina/6: ', this.courses.length / 6, ', this.courses.length%6: ', this.courses.length % 6)
      this.handleCurrentChange(1)
    },
    methods: {
      handleSizeChange (val) {
        console.log(val, 'items per page')
      },
      handleCurrentChange (val) {
        let prethodni
        this.filteredData = []
        let duzina = this.courses.length
        if (val * 6 < duzina) {
          duzina = val * 6
        }
        val -= 1
        let brojac = 0
        for (let i = val * 6; i < duzina; i++) {
          brojac++
          if (brojac > 6) {
            break
          }
          this.filteredData.push(this.courses[i])
          console.log('Dodan je: ', this.courses[i], ', i: ', i)
        }
        console.log('current page: ', val)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    width: 70%;
    margin: 0 auto;
    .courseCard {
      // width: 200px;
      margin-top: 20px;
      .image {
        max-height: 240px;
        width: 100%;
      }
    }
  }
  .el-pagination.is-background {
    white-space: nowrap;
    padding: 2px 5px;
    color: #303133;
    font-weight: 700;
    margin: 0 auto;
    text-align: center;
    margin-top: 30px;
    margin-bottom: 30px;
  }
</style>
