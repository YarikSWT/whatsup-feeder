<template>
  <section>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h1 class="mb-5">Подарки для любимых!</h1>
        </div>
        <div class="col-12 text-center">
          <h2 class="mb-4">На любой вкус и цвет</h2>
        </div>
        <el-row :gutter="30" class="w-100 my-5">
          <el-col
            v-for="(o, index) in presents"
            :key="index"
            :span="$mq !== 'sm' ? 8 : 24"
            class="content"
          >
            <el-card
              :body-style="{ padding: '0px', width: '350px' }"
              class="mb-4"
            >
              <img
                :src="require(`~/assets/img/${index}/${o.images[0]}`)"
                class="image w-100"
              />
              <div style="padding: 14px;">
                <div class="bottom clearfix">
                  <h5>{{ o.title }}</h5>
                  <!-- <p>{{ o.description }}</p> -->
                  <el-button
                    type="primary"
                    class="button mt-3"
                    @click="openCard(index)"
                    >Посмотреть</el-button
                  >
                </div>
              </div>
            </el-card>
          </el-col>
        </el-row>
      </div>
    </div>

    <el-dialog
      :title="presents[currentPresent].Title"
      :visible.sync="dialogVisible"
      :width="$mq !== 'sm' ? '50%' : '99%'"
    >
      <div>
        <el-carousel
          type="card"
          trigger="click"
          :height="$mq !== 'sm' ? '400px' : '120px'"
          :autoplay="false"
        >
          <el-carousel-item
            v-for="item in presents[currentPresent].images"
            :key="item"
            class="d-flex justify-content-center align-items-center"
          >
            <img
              class="h-100"
              :src="require(`~/assets/img/${currentPresent}/${item}`)"
              alt=""
            />
          </el-carousel-item>
        </el-carousel>
        <div>
          <h5>{{ presents[currentPresent].title }}</h5>
          <p>{{ presents[currentPresent].description }}</p>
        </div>
        <el-button type="primary" class="mt-4" @click="openWU"
          >Узнать подробнее</el-button
        >
      </div>
    </el-dialog>
  </section>
</template>

<script>
export default {
  data() {
    return {
      currentPresent: 0,
      presents: [
        {
          id: 0,
          title: 'СЕРДЦЕ для ЛЮБИМОЙ',
          description:
            'Любая выкладка из роз по Вашему желанию) + именное стихотворение на открытке+ плюшевый медвежонок',
          images: ['image.jpg', '0.jpg', '1.jpg', '2.jpg'],
        },
        {
          id: 1,
          title: 'Наш важный день ВИП',
          description:
            '35 роз в флористической губке в люльке + плюшевый медвежонок+ именное стихотворение Красные розы - Ред Наоми Белые розы - Аваланч Розовые розы-Ревиваль Кремовые розы -Талея Жёлтые розы - Пени Лейн Коралловые розы - Вау Алые розы - Эль Торо',
          images: ['0.jpg', '1.jpg', '2.jpg'],
        },
      ],
      dialogVisible: false,
    }
  },
  methods: {
    openCard(index) {
      this.currentPresent = index
      this.dialogVisible = true
    },
    openWU() {
      window.open(
        'https://api.whatsapp.com/send?phone=79191646801&text=Здравствуйте,%20Подскажите%20цену%20' +
          this.presents[this.currentPresent].title,
        '_self'
      )
    },
  },
}
</script>

<style>
.content {
  margin: 0 auto;
  max-width: 768px;
}

.sidebar {
  min-width: 300px;
}

@media (max-width: 767px) {
  .el-card__body {
    display: flex;
  }

  .el-card__body img {
    width: 140px !important;
  }
}
</style>
