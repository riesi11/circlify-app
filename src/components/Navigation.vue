<template>
    <div class="nav-links">
      <v-container>
        <v-img
            class="pa-0 pt-0"
            :aspect-ratio="1/1"
        >
          <img
              width="100"
              height="100"
              :src="require(`@/assets/logo.png`)" alt="">
        </v-img>
      </v-container>
    </div>
</template>

<script>

export default {
  name: "Navigation",
  components: {
  },
  data() {
    return {
      profileMenu: null,
      mobile: null,
      mobileNav: null,
      windowWidth: null,
    };
  },
  created() {
    window.addEventListener('resize', this.checkScreen);
    this.checkScreen()
  },
  methods:{
    checkScreen(){
      this.windowWidth = window.innerWidth;
      if (this.windowWidth <= 750) {
        this.mobile = true;
        return;
      }
      this.mobile = false;
      this.mobileNav = false;
      return;
    },
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
    },
    toggleProfileMenu(e){
      if(e.target === this.$refs.profile){
        this.profileMenu = !this.profileMenu;
      }
    },
  },
  computed: {

  }
}
</script>

<style lang="sass" scoped>
header
  background-color: rgb(0,0,0,0.1)
  padding: 0 25px
  box-shadow: 0 4px 6 px -1px rgb(0,0,0,0.1), 0 2px 4px -1px  rgb(0,0,0,0.60)
  z-index: 99
  .link
    font-weight: 500
    padding: 0
    transition: .3s color ease
    color: white
    &:hover
      color: #1eb8b8

  nav
    display: flex
    padding-top: 10px
    .branding
      display: flex
      align-items: center
      .header
        font-weight: 600
        font-size: 10px
        color: #000
        text-decoration: none
    .nav-links
      position: relative
      right: 0
      width: 250px
      display: flex
      flex: 1
      align-items: center
      justify-content: flex-end
      ul
        margin-right: 10px
        .link
          margin-right: 10px
        .link:last-child
          margin-right: 0

      .profile
        position: absolute
        cursor: pointer
        display: flex
        align-items: center
        justify-content: center
        width: 40px
        height: 40px
        border-radius: 50%
        color: #fff
        background-color: #303030

        span
          pointer-events: none

        .profile-menu
          position: absolute
          top: 60px
          right: 0
          width: 250px
          background-color: #303030
          box-shadow: 0 4px 6 px -1px rgb(0,0,0,0.1), 0 2px 4px -1px  rgb(0,0,0,0.60)

          .info
            display: flex
            align-items: center
            padding: 10px
            border-bottom: 1px solid #ffffff

            .initials
              position: initial
              width: 40px
              height: 40px
              background-color: #ffffff
              color: #303030
              display: flex
              align-items: center
              justify-content: center
              border-radius: 50%

            .right
              flex: 1
              margin-left: 24px

              p:nth-child(1)
                font-size: 14px
              p:nth-child(2),
              p:nth-child(3)
                font-size: 12px

          .options
            padding: 15px
            .option
              text-decoration: none
              color: #fff
              display: flex
              align-items: center
              margin-bottom: 12px
              .icon
                width: 18px
                height: auto
                color: #ffffff
              p
                font-size: 14px
                margin-left: 12px
              &:last-child
                margin-bottom: 0px
            .option:last-child
              margin-bottom: 0px


  .menu-icon
    cursor: pointer
    position: absolute
    top: 25px
    right: 25px
    height: 25px
    width: auto


</style>