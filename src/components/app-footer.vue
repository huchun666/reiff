<template>
  <div class="app-footer">
    <div class="app-footer-top">
      <div class="app-footer-top-left">
        <div class="app-footer-top-left-title">{{ $t('footer.aboutREIFFGroup') }}</div>
        <ul class="app-footer-top-left-ul" @click="handleRouter">
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 1}">{{ $t('footer.aboutUs') }}</li>
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 2}">{{ $t('footer.companies') }}</li>
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 3}">{{ $t('footer.cooperativePartners') }}</li>
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 4}">{{ $t('footer.companyPhilosophy') }}</li>
        </ul>
      </div>
      <div class="app-footer-top-left">
        <div class="app-footer-top-left-title">{{ $t('footer.legal') }}</div>
        <ul class="app-footer-top-left-ul" @click="handleRouter2">
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 5}">{{ $t('footer.copyrightInformation') }}</li>
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 6}">{{ $t('footer.generalTermsOfBusiness') }}</li>
          <li :class="{'app-footer-top-left-li-active': currentIndexFooter === 7}">{{ $t('footer.dataProtectionDeclaration') }}</li>
        </ul>
      </div>
      <div class="app-footer-top-right">
        <div class="app-footer-top-right-title">{{ $t('footer.contactUs') }}</div>
        <ul class="app-footer-top-right-ul">
          <li>{{ $t('footer.company') }}</li>
          <li>{{ $t('footer.location') }}</li>
          <li>{{ $t('footer.postcode') }}：201108</li>
          <li>{{ $t('footer.Tel') }}：{{ $t('footer.TelValue') }}</li>
          <li>{{ $t('footer.Fax') }}：{{ $t('footer.FaxValue') }}</li>
          <li>{{ $t('footer.Email') }}：shanghai@reiff-tp.cn</li>
        </ul>
      </div>
    </div>
    <div class="app-footer-bottom">
      <span>@2020 REIFF Technical Products Shanghai Co,. Ltd.</span>
      <a href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=31011202013081" target="_blank">
        <img src="../assets/images/footer/benanhao2.gif" alt="">
        <span>沪公网安备31011202013081号</span>
      </a>
      <a href="https://beian.miit.gov.cn" target="_blank">
        <span>沪ICP备202031752号-1</span>
      </a>
    </div>
  </div>
</template>

<script>
import { mapMutations, mapState } from 'vuex'
export default {
  data() {
    return {};
  },
  computed: {
    ...mapState(['currentIndexFooter'])
  },
  created() {},
  methods: {
    ...mapMutations(['setCurrentIndexFooter', 'setCurrentIndex']),
    handleRouter(e) {
      const { innerHTML } = e.target;
      let path = "";
      let currentPath = this.$route.path;
      if (innerHTML === "关于我们" || innerHTML === "About us") {
        this.setCurrentIndexFooter(1)
        path = "/history";
      }else if (innerHTML === "集团公司一览" || innerHTML === "Companies") {
        this.setCurrentIndexFooter(2)
        path = "/all-company";
      }else if (innerHTML === "合作伙伴" || innerHTML === "Cooperative partners") {
        this.setCurrentIndexFooter(3)
        path = "/cooperation";
      }else if (innerHTML === "公司理念" || innerHTML === "Company philosophy") {
        this.setCurrentIndexFooter(4)
        path = "/idea";
      }
      if (currentPath !== path) {
        this.setCurrentIndex(-1)
        scrollTo(0,0)
        this.$router.push({ path });
      }
    },
    handleRouter2(e) {
      const { innerHTML } = e.target;
      let path = "";
      let currentPath = this.$route.path;
      if (innerHTML === "版权信息" || innerHTML === "Copyright information") {
        this.setCurrentIndexFooter(5)
        path = "/copyright";
      }else if (innerHTML === "一般业务条款" || innerHTML === "General Terms of Business") {
        this.setCurrentIndexFooter(6)
        path = "/business-rule";
      }else if (innerHTML === "数据保护声明" || innerHTML === "Data protection declaration") {
        this.setCurrentIndexFooter(7)
        path = "/data-statement";
      }
      if (currentPath !== path) {
        this.setCurrentIndex(-1)
        scrollTo(0,0)
        this.$router.push({ path });
      }
    },
  },
  mounted() {},
};
</script>

<style scoped lang='scss'>
.app-footer {
  background: #f6f6f6;
}
.app-footer-top {
  display: flex;
  padding: 80px 0 60px 15%;
  color: #333;
  .app-footer-top-left {
    margin-right: 9.4vw;
  }
  .app-footer-top-left-title,
  .app-footer-top-right-title {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 20px;
    text-align: left;
  }
  .app-footer-top-left-ul {
    cursor: pointer;
    li {
      margin-bottom: 10px;
      font-size: 16px;
    }
    li:hover {
      color: #DB2C15;
    }
    .app-footer-top-left-li-active {
      color: #DB2C15;
    }
  }
  .app-footer-top-right-ul {
    font-size: 16px;
    color: #333;
    li {
      margin-bottom: 10px;
    }
  }
}
.app-footer-bottom {
  border-top: 1px solid #828282;
  padding-left: 15%;
  height: 77px;
  line-height: 77px;
  font-size: 16px;
  color: #333;
  display: flex;
  a {
    color: #333;
    margin-left: 40px;
    display: flex;
    align-items: center;
    img {
      width: 20px;
      height: 20px;
    }
  }
}
</style>