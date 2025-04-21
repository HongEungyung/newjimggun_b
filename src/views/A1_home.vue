<script setup>
import { ref, onMounted } from "vue";
import { Autoplay } from "swiper/modules";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/autoplay";
import { useRouter } from "vue-router";

const router = useRouter();

// top버튼
const smoothlyBtn = ref(null);
onMounted(() => {
  smoothlyBtn.value?.addEventListener("click", (e) => {
    e.preventDefault();
    window.scrollTo({
      top: 0,
      behavior: "smooth",
    });
  });
});
// 슬라이드 이미지 데이터
// 메인배너 더미데이터
const mainBannerData = ref([
  {
    id: 1,
    title1: "무거운 짐",
    title2: "짐꾼이 옮겨드립니다!",
    title3: "짐꾼은 무거운 여행짐을",
    title3Span: "집에서 숙소",
    title3After: "까지",
    title4Span: "",
    title4: "대신 들어드리는 여행 도우미 입니다.",
    image: "/images/hong/slideImg1.png",
    imageWidth: "400px",
  },
  {
    id: 2,
    title1: "간단한 예약",
    title2: "짐꾼은 많이 묻지 않습니다!",
    title3: "짐꾼의 몇 번의 클릭으로",
    title3Span: "빠르고 편리하게",
    title3After: "",
    title4Span: "",
    title4: "예약할 수 있습니다.",
    image: "/images/hong/slideImg2.png",
    imageWidth: "400px",
  },
  {
    id: 3,
    title1: "직접 찾아갑니다",
    title2: "간단하고 편리한 서비스!",
    title3: "짐꾼은 고객님이 앞에 두신 짐을",
    title3Span: "",
    title3After: "",
    title4Span: "직접 찾아가서",
    title4: " 수거해갑니다.",
    image: "/images/hong/slideImg3.png",
    imageWidth: "350px",
  },
  {
    id: 4,
    title1: "여행은 가볍게",
    title2: "짐꾼이 짐을 맡아드립니다!",
    title3: "짐꾼은 고객님의 소중한 짐을",
    title3Span: "",
    title3After: "",
    title4Span: "안전하게 보관",
    title4: " 해드립니다.",
    image: "/images/hong/slideImg4.png",
    image1: "/images/hong/slideImg4-1.png",
    imageWidth: "280px",
  },
]);
</script>

<template>
  <!-- gotop 버튼 -->
  <div class="topBtnWrap">
    <a href="#" class="topBtn" ref="smoothlyBtn">↑</a>
    <div class="resBtn" style="cursor: pointer">
      <img src="/images/hong/gotopBtn-logo-O.png" alt="gotopBtn로고" />
      <p>고용하기</p>
    </div>
    <!-- <div class="resBtn" @click="goToReservation" style="cursor: pointer">
      <img src="/images/hong/gotopBtn-logo-O.png" alt="gotopBtn로고" />
      <p>고용하기</p>
    </div>-->
  </div>

  <div class="main-wrap">
    <!-- 메인배너 슬라이드 -->
    <section class="visual">
      <!-- 메인베너 -->
      <Swiper :modules="[Autoplay]" :loop="true" :autoplay="{ delay: 3000 }">
        <SwiperSlide v-for="(slide, index) in mainBannerData" :key="index" class="slide">
          <div class="mainbannerText">
            <h1>{{ slide.title1 }}</h1>
            <h2>{{ slide.title2 }}</h2>
            <h3>
              {{ slide.title3 }}
              <span v-if="slide.title3Span">{{ slide.title3Span }}</span>
              {{ slide.title3After }}
            </h3>
            <h4>
              <span>{{ slide.title4Span }}</span>
              {{ slide.title4 }}
            </h4>
          </div>
          <div class="mainbannerImage">
            <img :src="slide.image" :alt="'슬라이드이미지' + slide.id" :style="{ width: slide.imageWidth }" :class="[slide.id === 3 ? 'mobile-img-3' : '', slide.id === 4 ? 'mobile-img-4' : '']" />
          </div>
        </SwiperSlide>
      </Swiper>
      <!-- 바로 예약하기 -->
      <div class="reservationMini">
        <form>
          <div class="mini-text mini-text1">
            <label for="mini1">출발지</label>
            <input type="text" id="mini1" placeholder="집 앞" />
          </div>
          <div class="mini-text mini-text1">
            <label for="mini1">짐 맡길 일정</label>
            <input type="text" id="mini1" placeholder="2025.03.21 / 10:00" />
          </div>
          <div class="mini-text mini-text1">
            <label for="mini1">도착지</label>
            <input type="text" id="mini1" placeholder="대구역" />
          </div>
          <div class="mini-text">
            <label for="mini1">짐 찾을 일정</label>
            <input type="text" id="mini1" placeholder="2025.03.22 / 11:00" />
          </div>
        </form>
        <div class="mini-button">
          <p>바로 예약</p>
        </div>
      </div>
    </section>
    <!-- 이용안내 -->
    <!-- 짐배송 영역 -->
    <section class="delivery-wrap">
      <!--  -->
      <!-- 1. 빠른 배송 서비스 -->
      <div class="fast-delivery inner">
        <h4 class="fast-dv-title">짐꾼의 빠른 <span>배송</span> 서비스</h4>
        <!-- 빠른 배송 서비스 순서 -->
        <ul class="fast-index">
          <li>
            <!-- <div class="a2-next-1"></div> -->
            <div class="fast-list1 fast-list">
              <h4>예약/결제</h4>
              <p>
                <span>예약 완료 시 <strong>카카오톡 알림</strong></span>
              </p>
              <div class="fast-line"></div>
              <div class="fast-icon">
                <span>01</span>
                <img src="/images/lee/fastIcon1.png" alt="예약/결제 이미지" />
              </div>
            </div>
            <!-- <div class="a2-next">
              <img src="/images/lee/nextstep.png" alt="화살표" />
            </div> -->
          </li>
          <li>
            <div class="fast-list2 fast-list">
              <h4>집앞 픽업</h4>
              <p>
                <strong>집앞</strong>에 짐을 두면 <br />
                짐꾼이 새벽픽업!
              </p>
              <div class="fast-line"></div>
              <div class="fast-icon">
                <span>02</span>
                <img src="/images/lee/fastIcon2.png" alt="집 앞 픽업" />
              </div>
            </div>
          </li>
          <li>
            <div class="fast-list3 fast-list">
              <h4>빠른 배송</h4>
              <p>
                체크인 시간까지 <br />
                짐꾼이 <strong>빠르게</strong> 배송!
              </p>
              <div class="fast-line"></div>
              <div class="fast-icon">
                <span>03</span>
                <img src="/images/lee/fastIcon3.png" alt="예약/결제 이미지" />
              </div>
            </div>
          </li>
          <li>
            <div class="fast-list4 fast-list">
              <h4>예약/결제</h4>
              <p>
                숙소와 상의 후 <br />
                <strong>안전한</strong> 장소에 도착!
              </p>
              <div class="fast-line"></div>
              <div class="fast-icon">
                <span>04</span>
                <img src="/images/lee/fastIcon4.png" alt="예약/결제 이미지" />
              </div>
            </div>
          </li>
        </ul>
      </div>
      <!--  -->
      <!-- 2. 배송 위치 -->
      <div class="dv-position">
        <ul class="position-list inner">
          <li class="pst-list1">
            <div class="title-icon">
              <h4 class="pst-title">집 - 숙소</h4>
              <ul class="pst-icon">
                <li><img src="/images/lee/house.png" alt="집아이콘" /></li>
                <li><img src="/images/lee/arrow.png" alt="화살표" /></li>
                <li>
                  <img src="/images/lee/arrival.png" alt="도착아이콘" />
                </li>
              </ul>
            </div>
            <ul class="pst-text">
              <li>1.가방은 문앞에! 픽업은 새벽에!</li>
              <li>2.체크인 시간에 맞춰 배송</li>
              <li>3.<span>비대면</span>으로 편리하게</li>
            </ul>
          </li>
          <li class="pst-list2">
            <div class="title-icon">
              <h4 class="pst-title">공항 - 집</h4>
              <ul class="pst-icon">
                <li>
                  <img src="/images/lee/airplane.png" alt="비행기아이콘" />
                </li>
                <li><img src="/images/lee/arrow.png" alt="화살표" /></li>
                <li><img src="/images/lee/house.png" alt="집아이콘" /></li>
              </ul>
            </div>
            <ul class="pst-text">
              <li>1.픽업한 가방은 무인보관함에!</li>
              <li>2.고객님의 <span>요청사항</span>에 맞춰 전달</li>
            </ul>
          </li>
          <li class="pst-list3">
            <div class="title-icon">
              <h4 class="pst-title">공항 - 숙소</h4>
              <ul class="pst-icon">
                <li>
                  <img src="/images/lee/airplane.png" alt="비행기아이콘" />
                </li>
                <li><img src="/images/lee/arrow.png" alt="화살표" /></li>
                <li>
                  <img src="/images/lee/arrival.png" alt="도착아이콘" />
                </li>
              </ul>
            </div>
            <ul class="pst-text">
              <li>1.공항 <span>무인보관함</span>에 짐 넣기</li>
              <li>2.체크인 시간에 맞춰 배송</li>
            </ul>
          </li>
        </ul>
        <div class="dv-position-bg"></div>
      </div>

      <!--  -->
    </section>
    <!-- 파트 1 -->
    <section class="a1-part1 inner">
      <div class="a1-part1-title">
        <h3>짐꾼 혜택</h3>
        <p>지금 받을 수 있는</p>
        <p>혜택을 확인해보세요.</p>
      </div>
      <ul class="a1-part1-boxes">
        <li class="part1-box1 part1-box">
          <div class="part1-img">
            <img src="/images/hong/s-banner-1.png" alt="혜택1" />
          </div>
          <div class="box-text box1-text">
            <h3>짐꾼 혜택 몰아보기</h3>
            <p>앱 다운로드 고객 한정 할인 중</p>
          </div>
        </li>
        <li class="part1-box2 part1-box">
          <div class="part1-img">
            <img src="/images/hong/s-banner-2.png" alt="혜택2" />
          </div>
          <div class="box-text box2-text">
            <h3>꼼꼼하게 지키는 짐꾼 케어</h3>
            <p>다양하게 보장되는 보험들을 체크해보세요</p>
          </div>
        </li>
        <li class="part1-box3 part1-box">
          <div class="part1-img">
            <img src="/images/hong/s-banner-3.png" alt="혜택3" />
          </div>
          <div class="box-text box3-text">
            <h3>Guid for Foreign Users</h3>
            <p>외국인 이용 가이드</p>
          </div>
        </li>
      </ul>
    </section>

    <!-- 파트 2 -->
    <section class="a1-part2">
      <!-- 파트2 - 제목 -->
      <div class="part2-title">
        <h3>여행가방 걱정 끝</h3>
        <p>짐꾼은 집앞에서 역/공항으로 역/공항에서 숙소로 여행짐을</p>
        <p>배송하는 캐리어 딜리버리 서비스입니다.</p>
      </div>

      <!-- 파트2 - 내용 -->
      <div class="part2-contents-all">
        <!-- 파트 2 웹 용 -->
        <div class="part2-web">
          <!-- 왼쪽 두개 -->
          <div class="part2-left">
            <!-- 1 -->
            <div class="p2-contents">
              <!-- 아이콘 -->
              <div class="p2-contents-icons">
                <img src="/images/hong/part2-icon1.png" alt="해외출장" />
                <h3>해외출장</h3>
              </div>
              <!-- 말풍선 글 1-->
              <div class="p2-contents-texts1 p2-underline">
                <h3>출장갈때, <span> 더 편하게 짐꾼! </span></h3>
                <p>
                  미팅 끝나고 가는 출장까지, <br />
                  짐은 짐꾼에 맡기고 두 손 가볍게 <br />이동하세요!
                </p>
              </div>
            </div>
            <!-- 2 -->
            <div class="p2-contents">
              <!-- 아이콘 -->
              <div class="p2-contents-icons">
                <img src="/images/hong/part2-icon2.png" alt="골프투어" />
                <h3>골프투어</h3>
              </div>
              <!-- 말풍선 글 2 -->
              <div class="p2-contents-texts2 p2-underline">
                <h3>골프투어도, <span> 더 즐겁게 짐꾼! </span></h3>
                <p>골프, 스쿠버다이빙, 서핑, 스키! <br />즐거운만큼 무거운 취미 용품들 <br />짐꾼이 안전하게 배송해드릴게요!</p>
              </div>
            </div>
          </div>

          <!-- 오른쪽 두개 -->
          <div class="part2-right">
            <!-- 3 -->
            <div class="p2-contents">
              <!-- 말풍선 글 3 -->
              <div class="p2-contents-texts3 p2-underline">
                <h3>주말여행 갈 때, <span> 더 빠르게 짐꾼! </span></h3>
                <p>짧은 주말을 이용해 떠나는 여행! <br />회사에 들고가자니 눈치보이는 <br />캐리어 짐꾼이 먼저 옮겨드릴게요!</p>
              </div>
              <!-- 아이콘 -->
              <div class="p2-contents-icons">
                <img src="/images/hong/part2-icon3.png" alt="주말여행" />
                <h3>주말여행</h3>
              </div>
            </div>
            <!-- 4 -->
            <div class="p2-contents">
              <!-- 말풍선 글 4 -->
              <div class="p2-contents-texts4 p2-underline">
                <h3>퇴근 후 여행, <span> 더 가볍게 짐꾼! </span></h3>
                <p>사람 많고, 정신없는 출근시간 <br />지옥철에 크고 무거운 캐리어와 <br />함께 타는 건 이제 그만!</p>
              </div>
              <!-- 아이콘 -->
              <div class="p2-contents-icons">
                <img src="/images/hong/part2-icon4.png" alt="퇴근여행" />
                <h3>퇴근여행</h3>
              </div>
            </div>
          </div>
        </div>

        <!-- 파트 2 768 용 -->
        <div class="part2-tablet">
          <!-- 1 -->
          <div class="t-content1">
            <!-- 아이콘 영역 -->
            <div class="t-1-icon">
              <img src="/public/images/hong/part2-icon1.png" alt="해외출장-T" />
              <h3>해외출장</h3>
            </div>
            <!-- 말풍선 영역 -->
            <div class="t-1-bubble">
              <h2>출장갈때, 더 편하게 짐꾼!</h2>
              <p>
                미팅 끝나고 가는 출장까지, <br />
                짐은 짐꾼에 맡기고 두 손 가볍게 <br />이동하세요!
              </p>
            </div>
          </div>
          <!-- 2 -->
          <div class="t-content2">
            <!-- 말풍선 영역 -->
            <div class="t-2-bubble">
              <h2>주말여행 갈 때, 더 빠르게 짐꾼!</h2>
              <p>짧은 주말을 이용해 떠나는 여행! <br />회사에 들고가자니 눈치보이는 <br />캐리어 짐꾼이 먼저 옮겨드릴게요!</p>
            </div>
            <!-- 아이콘 영역 -->
            <div class="t-2-icon">
              <img src="/public/images/hong/part2-icon3.png" alt="주말여행-T" />
              <h3>주말여행</h3>
            </div>
          </div>
          <!-- 3 -->
          <div class="t-content3">
            <!-- 아이콘 영역 -->
            <div class="t-1-icon">
              <img src="/public/images/hong/part2-icon2.png" alt="골프투어-T" />
              <h3>골프투어</h3>
            </div>
            <!-- 말풍선 영역 -->
            <div class="t-2-bubble">
              <h2>골프투어도, 더 즐겁게 짐꾼!</h2>
              <p>골프, 스쿠버다이빙, 서핑, 스키! <br />즐거운만큼 무거운 취미 용품들 <br />짐꾼이 안전하게 배송해드릴게요!</p>
            </div>
          </div>
          <!-- 4 -->
          <div class="t-content4">
            <!-- 말풍선 영역 -->
            <div class="t-2-bubble">
              <h2>퇴근 후 여행, 더 가볍게 짐꾼!</h2>
              <p>사람 많고, 정신없는 출근시간 <br />지옥철에 크고 무거운 캐리어와 <br />함께 타는 건 이제 그만!</p>
            </div>
            <!-- 아이콘 영역 -->
            <div class="t-2-icon">
              <img src="/public/images/hong/part2-icon4.png" alt="퇴근여행-T" />
              <h3>퇴근여행</h3>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 파트 3 -->
    <section class="a1-part3 inner">
      <!-- 첫번째 박스 -->
      <div class="part3-box1">
        <!-- 백그라운드 이미지 -->
        <!-- <div class="bgImg">
      <img src="/public/images/hong/part3-bg1.png" alt="">
      </div> -->

        <!-- 폰 이미지 -->
        <div class="phoneImg">
          <img src="/images/hong/part3-phoneImg.png" alt="폰 이미지" />
        </div>
        <!-- 텍스트 영역 전체 -->
        <div class="appTextPart">
          <div class="appTexts">
            <div class="appTexts-spans">
              <span class="jimggun-span">짐꾼</span>
              <span class="appdownload-span">앱 다운받기</span>
            </div>
            <p>여행가방 없이 떠나는 새로운 여행</p>
            <p>짐꾼에서 경험하세요!</p>
          </div>
          <!-- 다운로드 버튼들 -->
          <div class="downloadBtns">
            <!-- 안드로이드 -->
            <div class="androidBtn">
              <div class="androidBtnImg">
                <img src="/images/hong/p3-playstore.png" alt="플레이스토어 로고" />
                <span class="playstoreENG">Google Play</span>
              </div>
              <div class="androidBtnText">
                <span class="playstoreKOR">안드로이드</span>
                <span class="playstoreAdd">AOS</span>
              </div>
            </div>
            <!-- IOS -->
            <div class="appstoreBtn">
              <div class="appstoreBtnImg">
                <img src="/images/hong/p3-appstore.png" alt="플레이스토어 로고" />
                <span class="appstoreENG">App Store</span>
              </div>
              <div class="appstoreBtnText">
                <span class="appstoreIOS">IOS</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- 두번째 박스 -->
      <div class="part3-box2">
        <h3>짐꾼이 처음인 당신을 위한 쿠폰 혜택</h3>
        <p>신규회원 모두에게 가입 즉시 사용할 수 있는 쿠폰을 넣어드립니다.</p>
        <p>할인 혜택으로 여행을 가볍게 시작해보세요</p>
        <div class="couponImg">
          <img src="/images/hong/part3-coupon.png" alt="쿠폰 이미지" />
        </div>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
@import "/src/assets/variables";
.inner {
  max-width: 1240px;
  margin: 0 auto;
  padding: 0 20px;
}
.delivery-wrap {
  display: flex;
  flex-direction: column;
}
// 짐배송 영역
// 1. 빠른 배송 서비스
.fast-delivery {
  width: 100%;
  display: flex;
  flex-direction: column;
  @media screen and (max-width: 390px) {
    padding-top: 100px;
  }
  .fast-dv-title {
    font-weight: 600;
    font-size: $title-font-M;
    margin: 0 auto;
    margin-bottom: 70px;
    @media screen and (max-width: 390px) {
      margin-bottom: 30px;
      font-size: 30px !important;
    }
    span {
      color: $primary-color;
    }
    @media screen and (max-width: 768px) {
      font-size: $title-font-S;
    }
    @media screen and (max-width: 390px) {
      font-size: $title-font-XS;
    }
  }
  .fast-index {
    width: 100%;
    // min-width: 800px;
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 100px;
    align-items: center;
    justify-content: center;

    li {
      position: relative;
      width: calc(100% / 4);
      display: flex;
      align-items: center;
      justify-content: space-around;

      .fast-list {
        width: 90%;
        max-width: 240px;
        min-width: 160px;
        max-height: 326px;
        border: 1px solid rgba(229, 229, 236, 1);
        border-radius: 10px;
        box-shadow: $info-boxShadow;
      }
      .fast-list1,
      .fast-list2,
      .fast-list3 {
        &::after {
          content: "";
          position: absolute;
          top: 50%;
          right: 0;
          transform: translate(50%, -50%);
          display: block;
          width: 16px;
          height: 24px;
          background: url("/images/lee/nextstep.png");
        }
      }

      .fast-list1 {
        p {
          display: flex;
          align-items: center;
        }
      }
      div {
        padding: 0 25px;
        h4 {
          font-size: $text-font-XL;
          font-weight: bold;
          margin-top: 40px;
        }
        p {
          margin: 18px 0;
          font-size: $text-font-M;
          color: $font-gray;
          line-height: 1.4;
          min-height: 45px;
          strong {
            color: $font-primary;
            font-weight: 600;
          }
        }
        .fast-line {
          width: 100%;
          padding: 0 25px;
          height: 2px;
          background-color: $bg-light;
          margin: 0;
        }
        .fast-icon {
          display: flex;
          align-items: flex-start;
          justify-content: space-between;
          margin: 0;
          margin-top: 25px;
          padding: 0;
          span {
            font-weight: bold;
            font-size: $text-font-XL;
            color: $primary-color;
          }
          img {
            margin-top: 25px;
            margin-bottom: 30px;
          }
        }
      }
    }
  }
}
// 2. 배송위치
.dv-position {
  position: relative;
  width: 100%;
  background-color: $sub-color;
  .position-list {
    display: flex;
    justify-content: space-around;
    width: 100%;
    padding-top: 70px;
    > li {
      width: calc(100% / 3);
      max-width: 390px;
      display: flex;
      flex-direction: column;
      align-items: center;
      // justify-content: center;
      padding-bottom: 70px;
      .title-icon {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        .pst-title {
          padding-top: 55px;
          padding-bottom: 40px;
          font-size: $title-font-S;
          font-weight: bold;
          text-align: center;
        }
        .pst-icon {
          display: flex;
          align-items: center;
          justify-content: center;
          li {
            &:nth-child(2) {
              max-width: 44px;
            }
            &:first-child {
              min-width: 70px;
            }
            &:last-child {
              min-width: 70px;
            }
            img {
              width: 100%;
            }
          }
        }
      }
      .pst-text {
        padding-top: 55px;
        padding-bottom: 60px;
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 15px;
        li {
          width: 100%;
          max-width: 250px;
          font-weight: 500;
          font-size: $text-font-L;
          color: $font-gray;
          span {
            color: $primary-color;
            font-size: $text-font-XL;
            font-weight: bold;
          }
        }
      }
    }
  }
  .dv-position-bg {
    position: absolute;
    width: 100%;
    max-width: 5000px;
    // height: 100%;
    background-color: $sub-color;
    z-index: -1;
  }
}
// 반응형
@media screen and (max-width: 768px) {
  .fast-index li {
    width: calc(100% / 2) !important;
    max-width: 240px !important;
    margin-top: 20px;
  }
  .position-list {
    // flex-wrap: wrap !important;
    flex-direction: column !important;
    align-items: center !important;
  }
  .position-list > li {
    width: 100% !important;
    // width: calc(100% / 2) !important;
    flex-direction: row !important;
    align-items: center !important;
    justify-content: space-around;
    // gap: 30px;
    padding: 40px 0 !important;
    max-width: none !important;
    @media screen and (max-width: 390px) {
      flex-direction: column !important;
    }
  }
  .title-icon {
    gap: 20px;
  }
  .pst-title {
    padding: 0 !important;
    font-size: $title-font-XS !important;
  }
  .pst-text {
    padding: 0 !important;
  }
  .pst-icon {
    width: 70%;
    min-width: 180px;
  }
  .inqu-diff {
    padding-left: 0;
    padding-right: 0;
  }
  .inqu-diff-wrap {
    flex-direction: column !important;
    gap: 50px;
    position: relative;
    padding-left: 0;
    padding-right: 0;
  }
  .inquire,
  .diffcult {
    width: 100% !important;
    padding: 50px 30px;
  }
  .diffcult {
    // background-color: $sub-color;

    margin-top: 80px;
    position: relative;
  }
  .iq-textp,
  .dc-textp {
    font-size: 18px !important;
  }
  .iq-text span,
  .dc-text span {
    font-size: 20px !important;
  }
  .diff-bg {
    display: block !important;
    height: 50%;
    position: absolute;
    top: 50%;
    left: 0;
    background-color: $sub-color;
    z-index: -1;
  }
  .careful-title {
    font-size: $title-font-L !important;
  }
  .careful-list {
    font-size: $text-font-S !important;
  }
}
@media screen and (max-width: 600px) {
  .pst-title {
    font-size: $text-font-XL !important;
  }
  .pst-text li {
    font-size: $text-font-M !important;
  }
  .pst-text span {
    font-size: $text-font-L !important;
  }
  .inquire-menu,
  .diffcult-menu {
    gap: 30px !important;
  }
  .iq-textp,
  .dc-textp {
    font-size: $text-font-M !important;
  }
  .inquire-list,
  .diffcult-list {
    min-width: 360px;
    gap: 5px !important;
  }
  .dc-icon {
    width: 90px !important;
    height: 80px !important;
  }
  .iq-textp span,
  .dc-textp span {
    font-size: 18px !important;
  }
}
@media screen and (max-width: 500px) {
  .pst-title {
    font-size: $text-font-L !important;
  }
  .pst-text li {
    font-size: $text-font-S !important;
  }
  .pst-text span {
    font-size: $text-font-M !important;
  }
  .inquire,
  .diffcult {
    padding: 50px 10px;
  }
  .iq-textp,
  .dc-textp {
    font-size: $text-font-S !important;
  }
  .iq-textp span,
  .dc-textp span {
    font-size: 16px !important;
  }

  .careful-list {
    font-size: $text-font-XS !important;
  }
}
@media screen and (max-width: 450px) {
  .pst-text li {
    font-size: $text-font-XS !important;
  }
  .pst-text span {
    font-size: $text-font-S !important;
  }
  .pst-icon {
    width: 70%;
    min-width: 170px;
    @media screen and (max-width: 390px) {
      width: 100%;
    }
  }
  .pst-icon img {
    width: 90% !important;
  }
}
@media screen and (max-width: 430px) {
  .info-tap h3 span {
    font-size: $text-font-M !important;
  }
  .fast-list h4 {
    font-size: $text-font-L !important;
  }
  .fast-list p {
    font-size: $text-font-S !important;
  }
  .fast-list p span {
    font-size: $text-font-S !important;
  }
  .fast-icon span {
    font-size: $text-font-L !important;
  }
  .fast-list3 .fast-icon img {
    width: 90%;
  }
  .fast-icon img {
    width: 80%;
  }
}
@media screen and (max-width: 390px) {
  .inquire,
  .diffcult {
    padding: 50px 5px;
  }
}
// gotop 버튼
.topBtnWrap {
  position: fixed;
  right: 100px;
  bottom: 60px;
  z-index: 99999;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;

  .topBtn {
    color: $primary-color;
    font-size: 40px;
    text-decoration: none;
    width: 70px;
    height: 70px;
    line-height: 70px;
    border-radius: 50%;
    background-color: $white;
    text-align: center;
    box-shadow: $info-boxShadow;
  }
  .resBtn {
    width: 70px;
    height: 70px;
    border-radius: 50%;
    background-color: $white;
    border: 2px solid $primary-color;
    text-align: center;
    box-shadow: $info-boxShadow;
    text-decoration: none;
    padding: 13.5px 0;
    p {
      color: $primary-color;
      font-size: 12px;
      margin-bottom: 2px;
    }
  }
}
.main-wrap {
  width: 100%;

  // 메인베너
  .visual {
    width: 100%;
    position: relative;

    .swiper-wrapper {
      width: 100%;
      .slide {
        width: 100%;
        height: 32vw;
        min-height: 450px;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 100px;
        background-color: $bg-light;
        @media screen and (max-width: 1192px) {
          gap: 50px !important;
        }
        @media screen and (max-width: 768px) {
          height: auto !important;
          max-height: 600px !important;
          padding: 40px 20px 40px 20px !important;
          flex-direction: column !important;
          justify-content: space-between !important;
          gap: 1px !important;
        }
        @media screen and (max-width: 390px) {
          gap: 0 !important;
          padding: 20px 10px !important;
        }

        .mainbannerText {
          display: flex !important;
          flex-direction: column !important;
          gap: 8px;
          @media screen and (max-width: 768px) {
            text-align: left !important;
            gap: 4px !important;
            width: 100% !important;
            align-items: flex-start !important;
            max-width: 500px !important;
          }

          h1 {
            font-size: 35px;
            font-weight: 600;
            color: $primary-color;
            @media screen and (max-width: 1192px) {
              font-size: $title-font-M !important;
            }
            @media screen and (max-width: 968px) {
              font-size: $title-font-XS !important;
            }
            @media screen and (max-width: 768px) {
              font-size: 22px !important;
            }
            @media screen and (max-width: 390px) {
              font-size: 20px !important;
            }
          }
          h2 {
            font-size: 65px;
            font-weight: 800;
            margin-bottom: 12px;
            @media screen and (max-width: 1192px) {
              font-size: 50px !important;
            }
            @media screen and (max-width: 968px) {
              font-size: 36px !important;
            }
            @media screen and (max-width: 768px) {
              margin-bottom: 6px !important;
              line-height: 1.2 !important;
            }
            @media screen and (max-width: 390px) {
              font-size: 28px !important;
            }
          }
          h3 {
            font-size: $title-font-S;
            @media screen and (max-width: 1192px) {
              font-size: $text-font-M !important;
            }
            @media screen and (max-width: 768px) {
              font-size: 15px !important;
              line-height: 1.4 !important;
            }
            @media screen and (max-width: 390px) {
              font-size: 13px !important;
            }

            span {
              color: $primary-color;
              font-weight: 700;
            }
          }
          h4 {
            font-size: $title-font-S;
            @media screen and (max-width: 1192px) {
              font-size: $text-font-M !important;
            }
            @media screen and (max-width: 768px) {
              font-size: 15px !important;
              line-height: 1.4 !important;
            }
            @media screen and (max-width: 390px) {
              font-size: 13px !important;
            }

            span {
              color: $primary-color;
              font-weight: 700;
            }
          }
        }
        .mainbannerImage {
          display: flex;
          justify-content: center;
          align-items: center;
          @media screen and (max-width: 768px) {
            img.mobile-img-4 {
              transform: translateY(-20px) !important;
            }
            .mobile-img-3 {
              height: 95% !important;
            }
            .mobile-img-4 {
              width: 80% !important;
              max-width: 300px !important;
            }
          }
          @media screen and (max-width: 390px) {
            transform: translateY(-10px) !important;
            img.mobile-img-3 {
              transform: translateY(20px) !important;
            }
            img.mobile-img-4 {
              width: 70% !important;
              max-width: 300px !important;
              transform: translateY(-30px) !important;
            }
          }

          img {
            height: auto;
            object-fit: contain;
            @media screen and (max-width: 768px) {
              width: 80% !important;
              max-width: 480px !important;
            }
            @media screen and (max-width: 390px) {
              width: 90% !important;
              max-width: 320px !important;
              height: auto !important;
              margin-top: -10px !important;
            }
          }
        }
      }
    }
    // 바로 예약하기
    .reservationMini {
      width: 100%;
      max-width: 1000px;
      margin: 0 10px;
      padding-left: 15px;
      background-color: $white;
      border: 1px solid $bg-primary;
      border-radius: 50px;
      overflow: hidden;
      box-shadow: $reservation-boxShadow;
      display: flex;
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translate(-50%, 50%);
      z-index: 10;
      form {
        width: 100%;
        // max-width: 850px;
        display: flex;
        padding: 5px;
      }
      .mini-text1 {
        position: relative;
        &::after {
          content: "";
          display: block;
          width: 1px;
          height: 35px; // 선 높이
          background-color: $bg-primary;
          position: absolute;
          right: 0;
          top: 50%;
          transform: translateY(-55%);
        }
      }
      .mini-text {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 2px;
        width: calc(100% / 4);
        // padding: 10px;
        margin: 15px 0 10px 0;
        // border-left: 1px solid $bg-primary;
        &:first-of-type {
          border: none;
        }
        label {
          // width: 100px;
          // flex-shrink: 0;
          width: 85%;
          font-size: 14px;
          margin-right: 10px;
          padding-left: 20px;
          padding-right: 5px;
          font-weight: 500;
        }
        input {
          // flex: 1;
          width: 85%;
          border: none;
          outline: none;
          padding: 6px;
          margin-left: 15px;
          margin-right: 15px;
          border-radius: 6px;
          &::placeholder {
            color: $font-light-gray;
          }
          &:focus {
            background-color: $sub-color;
          }
        }
      }
      .mini-button {
        background-color: $primary-color;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 16%;
        cursor: pointer;
        // border-radius: 50px;
        // margin: 10px;
        p {
          font-size: $text-font-L;
          color: $white;
          font-weight: 700;
        }
      }
    }
  }

  /* part 1 */

  // 파트 1 전체
  .a1-part1 {
    display: flex;
    justify-content: space-between;
    padding: 100px 0;
    @media screen and (max-width: 390px) {
      display: block;
    }
    /* 타이틀 */
    .a1-part1-title {
      width: 25%;

      h3 {
        font-size: $title-font-M;
        font-weight: bold;
        margin-bottom: 15px;
      }
      p {
        line-height: 20px;
        color: $font-gray;
      }
    }
    /* 이미지 박스들 */
    /* ul */
    .a1-part1-boxes {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      width: 70%;
      gap: 20px;
      /* li */
      .part1-box {
        display: flex;
        flex-direction: column;
        flex-shrink: 0;
        width: calc(100% / 3);
        min-width: 180px;
        max-width: 300px;
        overflow: hidden;
        border: 1px solid $input-select;
        border-radius: 10px;
        cursor: pointer;

        .part1-img {
          width: 100%;
          // width: 300px;
          // height: 200px;

          img {
            width: 100%;
          }
        }
        .box-text {
          padding: 18px 18px 22px 18px;
          display: flex;
          flex-direction: column;
          h3 {
            font-size: $text-font-XL;
            font-weight: bold;
            margin-bottom: 8px;
          }
          p {
            font-size: $text-font-S;
            color: $font-gray;
          }
        }
      }
    }
  }

  //   part 2

  // 파트 2 전체
  .a1-part2 {
    background-color: $sub-color;
    padding: 100px 0;
    display: flex;
    flex-direction: column;
    gap: 50px;
    //   파트 2 제목
    .part2-title {
      text-align: center;
      h3 {
        font-size: $title-font-L;
        font-weight: bold;
        margin-bottom: 12px;
      }
      p {
        font-size: $text-font-XS;
        line-height: 16px;
        color: $font-gray;
      }
    }

    //  파트 2 내용
    .part2-contents-all {
      display: flex;
      justify-content: center;

      // 웹 용
      .part2-web {
        display: flex;
        align-items: center;
        gap: 75px;
        @media screen and (max-width: 768px) {
          display: none !important;
        }
        //   왼쪽 둘
        .part2-left {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          gap: 45px;
          // 1
          .p2-contents {
            display: flex;
            align-items: center;
            gap: 75px;
            // 아이콘
            .p2-contents-icons {
              display: flex;
              flex-direction: column;
              text-align: center;
              gap: 10px;
              width: 100px;
              img {
                width: 100%;
              }
              h3 {
                font-size: $title-font-S;
                font-weight: 600; //semibold
              }
            }
            // 말풍선 글 1
            .p2-contents-texts1 {
              background-color: $white;
              position: relative;
              width: 255px;
              padding: 30px;
              border-radius: 10px;
              border-bottom-left-radius: 0;
              &::after {
                content: "";
                position: absolute;
                bottom: 0;
                left: -30px;
                // transform: translateY(50%);
                transform: scaleX(-1);
                transform: scaleY(-1);
                width: 0;
                height: 0;
                border-left: 30px solid transparent;
                // border-right: 30px solid transparent;
                border-top: 25px solid $white;
              }
              h3 {
                font-size: $text-font-M;
                font-weight: 600;
                margin-bottom: 10px;
              }
              p {
                font-size: $text-font-S;
                line-height: 16px;
                color: $font-gray;
              }
            }
            // 말풍선 글 2
            .p2-contents-texts2 {
              background-color: $white;
              position: relative;
              width: 255px;
              padding: 30px;
              border-radius: 10px;
              border-top-left-radius: 0;
              &::after {
                content: "";
                position: absolute;
                top: 0;
                left: -30px;
                transform: scaleY(-1);
                width: 0;
                height: 0;
                border-left: 30px solid transparent;
                // border-right: 30px solid transparent;
                border-bottom: 25px solid $white;
              }
              h3 {
                font-size: $text-font-M;
                font-weight: 600;
                margin-bottom: 10px;
              }
              p {
                font-size: $text-font-S;
                line-height: 16px;
                color: $font-gray;
              }
            }
            // 말풍선 underline
            .p2-underline {
              span {
                position: relative;
                &::after {
                  content: "";
                  position: absolute;
                  left: -2%;
                  right: -2%;
                  bottom: 0;
                  height: 5px;
                  background-color: rgba(255, 111, 0, 0.5);
                }
              }
            }
          }
        }

        // 오른쪽 둘
        .part2-right {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          gap: 45px;
          // 3
          .p2-contents {
            display: flex;
            align-items: center;
            gap: 70px;
            // 아이콘
            .p2-contents-icons {
              display: flex;
              flex-direction: column;
              text-align: center;
              gap: 10px;
              width: 100px;
              img {
                width: 100%;
              }
              h3 {
                font-size: $title-font-S;
                font-weight: 600; //semibold
              }
            }
            // 말풍선 글 3
            .p2-contents-texts3 {
              background-color: $white;
              position: relative;
              width: 255px;
              padding: 30px;
              border-radius: 10px;
              border-bottom-right-radius: 0;
              &::after {
                content: "";
                position: absolute;
                bottom: 0;
                right: -30px;
                transform: translateY(-50%);
                transform: scaleY(-1);
                width: 0;
                height: 0;
                // border-left: 50px solid transparent;
                border-right: 30px solid transparent;
                border-top: 25px solid $white;
              }
              h3 {
                font-size: $text-font-M;
                font-weight: 600;
                margin-bottom: 10px;
              }
              p {
                font-size: $text-font-S;
                line-height: 16px;
                color: $font-gray;
              }
            }
            // 말풍선 글 4
            .p2-contents-texts4 {
              background-color: $white;
              position: relative;
              width: 255px;
              padding: 30px;
              border-radius: 10px;
              border-top-right-radius: 0;
              &::after {
                content: "";
                position: absolute;
                top: 0;
                right: -30px;
                transform: translateY(-50%);
                transform: scaleY(-1);
                width: 0;
                height: 0;
                // border-left: 50px solid transparent;
                border-right: 30px solid transparent;
                border-bottom: 25px solid $white;
              }
              h3 {
                font-size: $text-font-M;
                font-weight: 600;
                margin-bottom: 10px;
              }
              p {
                font-size: $text-font-S;
                line-height: 16px;
                color: $font-gray;
              }
            }
            // 말풍선 underline
            .p2-underline {
              span {
                position: relative;
                &::after {
                  content: "";
                  position: absolute;
                  left: -2%;
                  right: -2%;
                  bottom: 0;
                  height: 5px;
                  background-color: rgba(255, 111, 0, 0.5);
                }
              }
            }
          }
        }
      }

      // 768 용
      .part2-tablet {
        display: none;
        height: auto;
        // display: flex;
        flex-direction: column;
        gap: 50px;
        @media screen and (max-width: 768px) {
          display: flex !important;
          flex-direction: column !important;
          gap: 50px !important;
        }
        @media screen and (max-width: 390px) {
          width: 350px;
        }
        // 1
        .t-content1 {
          display: flex;
          align-items: center;
          gap: 75px;
          @media screen and (max-width: 390px) {
            gap: 15px;
          }
        }
        // 2
        .t-content2 {
          display: flex;
          align-items: center;
          gap: 75px;
          @media screen and (max-width: 390px) {
            gap: 15px;
          }
        }
        // 3
        .t-content3 {
          display: flex;
          align-items: center;
          gap: 75px;
          @media screen and (max-width: 390px) {
            gap: 15px;
          }
        }
        // 4
        .t-content4 {
          display: flex;
          align-items: center;
          gap: 75px;
          @media screen and (max-width: 390px) {
            gap: 15px;
          }
        }
        // 왼쪽 아이콘 영역
        .t-1-icon {
          display: flex;
          flex-direction: column;
          text-align: center;
          gap: 10px;
          width: 100px;
          img {
            width: 100%;
          }
          h3 {
            font-size: $title-font-S;
            font-weight: 600; //semibold
            @media screen and (max-width: 390px) {
              font-size: 20px;
            }
          }
        }
        // 왼쪽 말풍선 영역
        .t-1-bubble {
          background-color: $white;
          position: relative;
          width: 255px;
          padding: 30px;
          border-radius: 10px;
          border-bottom-left-radius: 0;
          @media screen and (max-width: 390px) {
            border-radius: 0px;
            padding: 15px;
          }
          &::after {
            content: "";
            position: absolute;
            bottom: 0;
            left: -30px;
            transform: scaleX(-1);
            transform: scaleY(-1);
            width: 0;
            height: 0;
            border-left: 30px solid transparent;
            border-top: 25px solid $white;
            @media screen and (max-width: 390px) {
              display: none;
            }
          }
          h2 {
            font-size: $text-font-M;
            font-weight: 600;
            margin-bottom: 10px;
          }
          p {
            font-size: $text-font-S;
            line-height: 16px;
            color: $font-gray;
          }
        }
        // 오른쪽 말풍선 영역
        .t-2-bubble {
          background-color: $white;
          position: relative;
          width: 255px;
          padding: 30px;
          border-radius: 10px;
          border-bottom-right-radius: 0;
          @media screen and (max-width: 390px) {
            border-radius: 0px;

            padding: 15px;
          }

          &::after {
            content: "";
            position: absolute;
            bottom: 0;
            right: -30px;
            transform: translateY(-50%);
            transform: scaleY(-1);
            width: 0;
            height: 0;
            // border-left: 50px solid transparent;
            border-right: 30px solid transparent;
            border-top: 25px solid $white;
            @media screen and (max-width: 390px) {
              display: none;
            }
          }
          h2 {
            font-size: $text-font-M;
            font-weight: 600;
            margin-bottom: 10px;
          }
          p {
            font-size: $text-font-S;
            line-height: 16px;
            color: $font-gray;
          }
        }
        // 오른쪽 아이콘 영역
        .t-2-icon {
          display: flex;
          flex-direction: column;
          text-align: center;
          gap: 10px;
          width: 100px;
          img {
            width: 100%;
          }
          h3 {
            font-size: $title-font-S;
            font-weight: 600; //semibold
            @media screen and (max-width: 390px) {
              font-size: 20px;
            }
          }
        }
      }
      // 390용
    }
  }
  // part 3

  // 파트3 전체
  .a1-part3 {
    margin-top: 100px;
    margin-bottom: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    // background-color: aqua;
    // 파트 3 - 첫번째 박스
    .part3-box1 {
      background: url("/public/images/hong/part3-bg1.png") center center / cover no-repeat;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 45px;
      width: 55%;
      height: 407px;

      // 폰이미지
      .phoneImg {
        width: 150px;
        img {
          margin-top: 18px;
          width: 100%;
          display: block;
        }
      }
      // 텍스트 영역 전체
      .appTextPart {
        // 텍스트
        .appTexts {
          .appTexts-spans {
            margin-bottom: 10px;
            .jimggun-span {
              font-size: 32px;
              color: $white;
              margin-right: 5px;
            }
            .appdownload-span {
              font-size: 32px;
              font-weight: 700;
              color: $white;
            }
          }
          p {
            font-size: $text-font-S;
            color: $white;
            line-height: 17px;
            &:last-child {
              margin-bottom: 20px;
            }
          }
        }
        // 다운로드 버튼들
        .downloadBtns {
          display: flex;
          flex-direction: column;
          gap: 10px;
          // 안드로이드
          .androidBtn {
            background-color: $white;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 50px;
            padding: 15px 30px;
            border-radius: 6px;
            width: 100%;
            max-width: 300px;
            cursor: pointer;
            .androidBtnImg {
              display: flex;
              align-items: center;
              img {
                width: 24px;
                margin-right: 5px;
              }
            }
            .androidBtnText {
              display: flex;
              justify-content: space-between;
              .playstoreKOR {
                color: $primary-color;
                font-weight: 700;
              }
              .playstoreAdd {
                display: none;
              }
            }
          }
          // IOS
          .appstoreBtn {
            background-color: $white;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 50px;
            padding: 15px 30px;
            border-radius: 6px;
            width: 100%;
            max-width: 300px;
            cursor: pointer;
            .appstoreBtnImg {
              display: flex;
              align-items: center;
              img {
                width: 23px;
                margin-right: 7px;
              }
            }
            .appstoreBtnText {
              display: flex;
              justify-content: space-between;
              span {
                color: $primary-color;
                font-weight: 700;
              }
            }
          }
        }
      }
    }
    // 파트 3 - 두번째 박스
    .part3-box2 {
      background: url("/public/images/hong/part3-bg2.png") center center / cover no-repeat;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 45%;
      height: 407px;
      h3 {
        font-size: $title-font-XS;
        font-weight: 700;
        margin-bottom: 9px;
        line-height: 1.4;
      }
      p {
        font-size: $text-font-XS;
        line-height: 14px;
        color: $font-gray;
        @media screen and (max-width: 390px) {
          line-height: 10px;
        }
      }
      .couponImg {
        margin-top: 18px;
        width: 100%;
        max-width: 300px;
        cursor: pointer;
        img {
          width: 100%;
          display: block;
        }
      }
    }
  }
}
@media screen and (max-width: 1500px) {
}
@media screen and (max-width: 1250px) {
  .box-text h3 {
    font-size: $text-font-L !important;
  }
  .box-text p {
    font-size: $text-font-XS !important;
  }
}
@media screen and (max-width: 1115px) {
  .box-text h3 {
    font-size: $text-font-M !important;
  }
  .box-text p {
    font-size: $text-font-XS !important;
  }
}
@media screen and (max-width: 1011px) {
  .box1-text p {
    margin-bottom: 12px !important;
  }
  .box3-text p {
    margin-bottom: 12px !important;
  }
}
@media screen and (max-width: 990px) {
  .box-text h3 {
    font-size: $text-font-S !important;
  }
  .box-text p {
    font-size: $text-font-XS !important;
  }
}
@media screen and (max-width: 937px) {
  .playstoreKOR {
    display: none !important;
  }
  .playstoreAdd {
    color: $primary-color !important;
    font-weight: 700 !important;
    display: block !important;
  }
}
@media screen and (max-width: 881px) {
}
@media screen and (max-width: 871px) {
  .a1-part3 {
    display: flex !important;
    flex-direction: column !important;
  }
  .part3-box1 {
    width: 100% !important;
  }
  .part3-box2 {
    width: 100% !important;
  }
}
@media screen and (max-width: 867px) {
}
@media screen and (max-width: 859px) {
  .a1-part1-title h3 {
    font-size: 24px !important;
  }
  .a1-part1-title p {
    font-size: 14px !important;
    line-height: 18px !important;
  }
}
@media screen and (max-width: 801px) {
  .box1-text h3 {
    margin-bottom: 22px !important;
  }
  .box2-text h3 {
    margin-bottom: 22px !important;
  }
}
@media screen and (max-width: 784px) {
  .box2-text h3 {
    margin-bottom: 8px !important;
  }
}
@media screen and (max-width: 768px) {
  // gotop 버튼
  .topBtnWrap {
    // display: none !important;
    right: 15px;
  }
  // 파트1 영역
  .a1-part1 {
    display: flex !important;
    flex-direction: column !important;
    justify-content: center !important;
    align-items: center !important;
    gap: 15px;
    margin: 0 !important;
    padding: 100px 20px !important;
  }
  .a1-part1-title h3 {
    text-align: center !important;
  }
  .a1-part1-title p {
    text-align: center !important;
  }
  .a1-part1-boxes {
    width: 100% !important;
  }
  .box1-text h3 {
    margin-bottom: 8px !important;
  }
  .box1-text p {
    margin-bottom: unset !important;
  }
  .box3-text p {
    margin-bottom: unset !important;
  }
  // 예약미니 바
  .reservationMini {
    display: none !important;
  }
}
@media screen and (max-width: 751px) {
  .box1-text p {
    margin-bottom: 12px !important;
  }
  .box3-text p {
    margin-bottom: 12px !important;
  }
}
@media screen and (max-width: 634px) {
  .a1-part1-boxes {
    display: flex !important;
    flex-direction: column !important;
    gap: 8px !important;
  }
  .a1-part1-title p {
    display: none !important;
  }
  .part1-box {
    display: flex !important;
    flex-direction: row !important;
    width: 100% !important;
    min-width: 165px !important;
    max-width: unset !important;
    gap: 10px !important;
    // max-height: 61px;
  }
  .part1-img {
    // width: 50% !important;
    // width: 140px !important;
    flex: 1 !important;
    // object-fit: cover !important;
  }
  .part1-img img {
    display: block !important;
    width: 100% !important;
  }
  .box-text {
    flex: 2 !important;
    display: flex !important;
    flex-direction: column !important;
    justify-content: center !important;
    align-items: flex-start !important;
    padding: 10px !important;
  }
  .box-text h3 {
    font-size: 18px !important;
  }
  .box-text p {
    font-size: 16px !important;
  }
}
@media screen and (max-width: 550px) {
  // 파트 3 영역
  .part3-box1 {
    display: flex !important;
    flex-direction: column !important;
    justify-content: center !important;
    align-items: center !important;
    width: 100% !important;
    gap: 0 !important;
  }
  .phoneImg img {
    display: none !important;
  }
  .part3-box2 {
    width: 100%;
  }
}
@media screen and (max-width: 475px) {
  .box-text h3 {
    font-size: 14px !important;
  }
  .box-text p {
    font-size: 12px !important;
  }
}
@media screen and (max-width: 403px) {
  .a1-part1-title {
    width: 200px !important;
    margin: auto;
  }
  .a1-part1-title h3 {
    font-size: 30px !important;
  }
  .part1-img {
    flex: 1.7 !important;
  }
}
</style>
