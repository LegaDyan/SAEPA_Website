<template lang="pug">
#home
  .triangle
  jumbotron
  .container
    .first
      .aboutUs
        .aboutTitle.
          {{ aboutus.title }}<br>—
        .aboutContent {{ aboutus.text }}
      .icon_container
        .icon_box(v-for="item in aboutus.list")
          img(:src="item.url", :alt="item.alt")
          .icon_text
            p {{ item.text1 }}
            p {{ item.text2 }}
            p —
    .projects
      .intro
        .summary
          img.paddingB(src="../images/book.png")
          div.
            2006年，协会由主要来自2006年中美暑期联合支教实践活动的支队长发起，在清华大学扶贫办公室大力支持与帮助下，成立了最初的教育扶贫志愿者协会。<br>
            之后，在学校社团部注册时，正式更名为清华大学学生教育扶贫公益协会，<br>
            "Student Association of Educational Poverty Alleviation" ——SAEPA。
        .achievements
          .picSide
            img(src="../images/cx1.png", alt="创新工作室")
          .textSide.borderTop(:style="{ background: textSides[0] }")
            .textTitle 创新工作室
            div.
              <br>
              实践公益新想法<br>
              探索公益新领域
          .picSide
            img(src="../images/cx2.png", alt="创新工作室")
        .achievements
          .picSide.picLSide
            img(src="../images/dnca1.png", alt="电脑传爱")
          .picSide.picRSide
            img(src="../images/dnca2.png", alt="电脑传爱")
          .textSide(:style="{ background: textSides[1] }")
            .textTitle 电脑传爱
            div.
              <br>
              互联网+科技+公益
        .achievements
          .textSide(:style="{ background: textSides[2] }")
            .textTitle 梦想课堂
            div.
              <br>
              梦想<br>
              是给孩子最好的礼物
          .picSide.picLSide
            img(src="../images/mxkt1.png", alt="梦想课堂")
          .picSide.picRSide
            img(src="../images/mxkt2.png", alt="梦想课堂")
        .achievements
          .picSide
            img(src="../images/zmzj1.png", alt="周末支教")
          .textSide(:style="{ background: textSides[3] }")
            .textTitle 周末支教
            div.
              <br>
              用周末不长的时间<br>
              做一生难忘的事情
          .picSide
            img(src="../images/zmzj2.png", alt="周末支教")
</template>

<script>
import Jumbotron from '@/components/Jumbotron';
import tex1 from '@/images/home/text1.jpg';
import tex2 from '@/images/home/text2.jpg';
import tex3 from '@/images/home/text3.jpg';
import tex4 from '@/images/home/text4.jpg';
import { home } from '../data.json';

export default {
  name: 'home',
  components: {
    Jumbotron,
  },
  data() {
    const addBG = img => `url(${img}) no-repeat center center`;
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationClickable: true,
      },
      aboutus: home.aboutus,
      textSides: [
        addBG(tex1),
        addBG(tex2),
        addBG(tex3),
        addBG(tex4),
      ],
    };
  },
};
</script>


<style lang="scss" scoped>
.triangle {
  border-left: 100px solid transparent;
  border-right: 100px solid transparent;
  border-top: 40px solid #f8f9fb;
  position: absolute;
  top: 80px;
  left: calc(100vw / 2 - 100px);
  z-index: 5;
}

.jumbotron {
  height: calc(100vh - 82px);
  max-height: calc(100vw * 9 / 16);
}

.first {
  padding: 30px 100px;
  .aboutUs {
    text-align: center;
    .aboutTitle {
      padding: 30px 0;
      font-size: 30px;
      color: #612379;
    }
    .aboutContent {
      font-size: 16px;
      line-height: 25px;
      padding-bottom: 30px;
      color: #646466;
    }
  }
  .icon_container {
    font-size: 18px;
    color: #612379;
    margin-top: 70px;
    display: flex;
    justify-content: center;
    .icon_box {
      text-align: center;
      padding: 0 55px;
      img {
        width: 85%;
      }
    }
  }
}

.paddingB {
  padding-bottom: 50px;
}

.intro {
  .summary {
    text-align: center;
    font-size: 20px;
    color: white;
    padding: 70px;
    background: url("../images/1.jpg") no-repeat center center;
    background-size: cover;
    -webkit-background-size: cover;
    img {
      width: 150px;
      height: 100px;
    }
  }
  .achievements {
    display: flex;
    .picSide, .textSide {
      height: calc(100vw / 3 * 280 / 400);
    }
    .picSide {
      width: 33.333333%;
      img {
        width: 100%;
      }
      overflow: hidden;
    }
    .picLSide {
      margin-right:0;
    }
    .picRSide {
      margin-left: 0;
    }
    .textSide {
      background-size: cover;
      -webkit-background-size: cover;
      color: white;
      width: 33.333333%;
      text-align: center;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      .textTitle {
        font-size: 25px;
        font-weight: bold;
      }
    }
  }
}

@media only screen and (max-width: 768px) {
  .triangle {
    display: none;
  }
  .intro {
    /*margin-top: 40px;*/
    /*padding: 0;*/
    .achievements .picSide {
      padding: 0;
      margin: 0;
    }
    font-size: 11px;
    .achievements .textSide .textTitle {
      font-size: 15px;
    }
    .summary {
      font-size: 14px;
      padding: 50px;
      img {
        width: 70px;
        height: 50px;
        padding: 10px;
      }
    }
  }
  .first {
    padding: 15px;
    .icon_container {
      font-size: 12px;
      margin-top: 40px;
      .icon_box {
        padding: 0;
        img {
          width: 75%;
        }
      }
    }
  }
}
</style>
