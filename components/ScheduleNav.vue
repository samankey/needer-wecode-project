<!-- Please remove this file from your project -->
<template>
  <div>
    <div class="topSolid"></div>
    <div class="navWrapper">
      <div class="logo">
        <img
          src="https://www.gubgoo.com/img/new_img/Main_Logo_B.png"
          alt="logo"
        />
      </div>
      <div class="menu">
        <p>SCHEDULE</p>
      </div>
      <div class="userInfo">
        <div class="userPicture">
          <p>S</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.topSolid {
  height: 30px;
  background-color: rgb(37, 66, 233);
}

.navWrapper {
  display: flex;
  justify-content: space-between;
  padding: 10px 30px;
  background-color: #fff;
  border-bottom: 1px solid rgb(219, 219, 219);

  .logo {
    display: flex;
    align-items: center;

    img {
      width: 60px;
    }
  }

  .menu {
    display: flex;
    align-items: center;

    p {
      font: {
        size: 20px;
        weight: 700;
      }
      color: rgb(59, 59, 59);
      /* letter-spacing: 10px; */
    }
  }

  .userInfo {
    display: flex;
    align-items: center;

    .userPicture {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 40px;
      height: 40px;
      border-radius: 999px;
      background-color: rgb(255, 121, 44);

      p {
        color: #fff;
        font: {
          size: 20px;
          weight: 700;
        }
      }
    }
  }
}
</style>
