<template>
  <section>
    <div
      class="bg position-relative overflow-hidden p-3 p-md-5 m-md-3 text-center bg-light"
    >
      <div class="col-md-5 p-lg-5 mx-auto my-5 head_text" style="">
        <h1 class="display-4 font-weight-normal">Подарки для любимых</h1>
        <p class="lead font-weight-normal">
          На любой вкус и цвет от DnD Group
        </p>
        <a
          class="btn btn-outline-secondary"
          href="https://api.whatsapp.com/send?phone=79191646801&text=Здравствуйте,%20Подскажите%20цену%20Цветов"
          >Узнать</a
        >
      </div>
      <div class="product-device box-shadow d-none d-md-block"></div>
      <div
        class="product-device product-device-2 box-shadow d-none d-md-block"
      ></div>
    </div>
    <div class="container">
      <div class="row">
        <el-row :gutter="30" class="w-100 my-5">
          <el-col
            v-for="(o, index) in presents"
            :key="index"
            :span="$mq !== 'sm' ? 8 : 24"
            class="content"
          >
            <el-card :body-style="{ padding: '0px' }" class="mb-4">
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
        <div v-for="i in 21" :key="i" class="col-12 col-md-4 col-lg-4">
          <img
            class="w-100 mb-3"
            :src="require(`~/assets/img/${i}.JPG`)"
            alt=""
          />
        </div>
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
        {
          id: 2,
          title: 'Наш важный день',
          description:
            '35 роз в флористической губке в люльке + плюшевый медвежонок+ именное стихотворение Красные розы - Ред Наоми Белые розы - Аваланч Розовые розы-Ревиваль Кремовые розы -Талея Жёлтые розы - Пени Лейн Коралловые розы - Вау Алые розы - Эль Торо Пионовидные розы - Мисти Баблс',
          images: ['0.jpg', '1.jpg', '2.jpg', '3.jpg', '4.jpg'],
        },
        {
          id: 3,
          title: 'Поздравление для любимой',
          description:
            '51 роза в коробке или корзине + мишка + трогательное именное стихотворение Красные розы - Ред Наоми Белые розы - Аваланч Розовые розы-Ревиваль Кремовые розы -Талея Жёлтые розы - Пени Лейн Коралловые розы - Вау',
          images: ['0.jpg', '1.jpg', '2.jpg', '3.jpg'],
        },
        {
          id: 4,
          title: 'Благодарность за малыша',
          description:
            '25 роз в шляпной коробке+ стих с именами супруги и малыша+ плюшевый медвежонок Красные розы - Ред Наоми Белые розы - Аваланч Розовые розы-Ревиваль Кремовые розы -Талея Жёлтые розы - Пени Лейн Коралловые розы - Вау Алые розы - Эль Торо',
          images: ['0.jpg', '1.jpg', '2.jpg'],
        },
        {
          id: 5,
          title: 'Спасибо за счастье...',
          description:
            '35 роз в шляпной коробке + мишка + трогательное стихотворение Красные розы - Ред Наоми Белые розы - Аваланч Розовые розы-Ревиваль Кремовые розы -Талея Жёлтые розы - Пени Лейн Коралловые розы - Вау Алые розы - Эль Торо',
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

.bg {
  background-image: url('../assets/img/2.JPG');
  background-repeat: no-repeat;
  background-position: center;
}

.head_text {
  height: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: rgb(248, 247, 250, 0.8);
  border-radius: 10px;
}

.sidebar {
  min-width: 300px;
}

.el-card__body {
  /* width: 350px; */
}

.el-card__body img {
  height: 290px;
  object-fit: scale-down;
}

@media (max-width: 767px) {
  .el-card__body {
    display: flex;
    width: 100%;
  }

  .el-card__body img {
    width: 140px !important;
    height: 100%;
  }

  .el-row {
    margin-left: 0 !important;
    margin-right: 0 !important;
  }
}
</style>
