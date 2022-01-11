<template>
  <el-tabs v-model="activeName" class="tabs">
    <el-tab-pane label="生码" name="first">
      <div class="raw-code">
        <div class="flex">
          <el-input placeholder="请输入内容" v-model="rawCode"> </el-input>
          <el-button type="primary" @click="handleClick" plain>生码</el-button>
        </div>
        <div class="qrcode" ref="qrCodeUrl" id="qrcode"></div>
        <el-button type="primary" class="download " plain @click="download"
          >下载图片</el-button
        >
      </div>
    </el-tab-pane>
    <el-tab-pane label="解码" name="second">
      <div class="decoding">
        <el-button @click="handleResult" plain>点击解码</el-button>
        <video autoplay></video>

        <div class="app__overlay">
          <div class="app__overlay-frame"></div>
          <!-- Scanner animation -->
          <svg
            class="app__scanner-img"
            width="260"
            height="260"
            viewBox="0 0 215 215"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
          >
            <g
              id="Page-1"
              stroke="none"
              stroke-width="1"
              fill="none"
              fill-rule="evenodd"
            >
              <g
                id="Artboard"
                transform="translate(-146.000000, -58.000000)"
                fill="#7e7a7a"
                fill-rule="nonzero"
              >
                <g id="scanner" transform="translate(146.000000, 58.000000)">
                  <path
                    d="M169.272388,200.559701 L169.272388,194.141791 L169.272388,200.559701 Z M206.977612,169.272388 L213.395522,169.272388 L206.977612,169.272388 Z M197.751866,196.548507 L195.386866,194.380056 L197.751866,196.548507 Z M177.294776,215 C182.766045,215 188.646455,214.846772 193.977332,213.800653 C199.295373,212.757743 204.460187,210.752948 208.139254,206.739347 L203.409254,202.402444 C201.047463,204.977631 197.426959,206.583713 192.741884,207.503078 C188.07125,208.420037 182.731549,208.58209 177.294776,208.58209 L177.294776,215 Z M208.139254,206.739347 C211.515877,203.057071 213.159664,197.946007 214.013246,192.871045 C214.876455,187.740728 215,182.195653 215,177.294776 L208.58209,177.294776 C208.58209,182.153134 208.452127,187.240933 207.684384,191.806474 C206.907015,196.426567 205.543209,200.074347 203.409254,202.402444 L208.139254,206.739347 L208.139254,206.739347 Z M200.559701,37.7052239 L194.141791,37.7052239 L200.559701,37.7052239 Z M196.548507,9.22574627 L194.380056,11.5907463 L196.548507,9.22574627 Z M215,37.7052239 C215,32.2339552 214.846772,26.3535448 213.800653,21.0226679 C212.757743,15.7046269 210.752948,10.5398134 206.739347,6.86074627 L202.402444,11.5907463 C204.977631,13.9525373 206.583713,17.573041 207.503078,22.2581157 C208.420037,26.9295522 208.58209,32.2684515 208.58209,37.7052239 L215,37.7052239 Z M206.739347,6.86074627 C203.057071,3.48412313 197.946007,1.84033582 192.871045,0.986753731 C187.740728,0.123544776 182.195653,5.32907052e-15 177.294776,5.32907052e-15 L177.294776,6.41791045 C182.153134,6.41791045 187.240933,6.54787313 191.806474,7.31561567 C196.426567,8.09298507 200.074347,9.45759328 202.402444,11.5915485 L206.739347,6.86074627 Z M6.41791045,169.272388 L12.8358209,169.272388 L6.41791045,169.272388 Z M37.7052239,206.977612 L37.7052239,213.395522 L37.7052239,206.977612 Z M10.4291045,197.751866 L12.597556,195.386866 L10.4291045,197.751866 Z M-2.39808173e-14,177.294776 C-2.39808173e-14,182.766045 0.152425373,188.646455 1.19934701,193.977332 C2.24225746,199.295373 4.24705224,204.460187 8.26065299,208.139254 L12.597556,203.409254 C10.0223694,201.047463 8.41628731,197.426959 7.49692164,192.741884 C6.57996269,188.07125 6.41791045,182.731549 6.41791045,177.294776 L-2.39808173e-14,177.294776 Z M8.26065299,208.139254 C11.9429291,211.515877 17.0539925,213.159664 22.1289552,214.013246 C27.2600746,214.876455 32.8051493,215 37.7052239,215 L37.7052239,208.58209 C32.8468657,208.58209 27.7590672,208.452127 23.1943284,207.684384 C18.5734328,206.907015 14.925653,205.543209 12.597556,203.409254 L8.26065299,208.139254 L8.26065299,208.139254 Z M37.7052239,6.41791045 L37.7052239,12.8358209 L37.7052239,6.41791045 Z M9.22574627,10.4291045 L11.5907463,12.597556 L9.22574627,10.4291045 Z M37.7052239,0 C32.2339552,0 26.3535448,0.152425373 21.0226679,1.19934701 C15.7046269,2.24225746 10.5398134,4.24705224 6.86074627,8.26065299 L11.5907463,12.597556 C13.9525373,10.0223694 17.573041,8.41628731 22.2581157,7.49692164 C26.9295522,6.57996269 32.2684515,6.41791045 37.7052239,6.41791045 L37.7052239,0 Z M6.86074627,8.26065299 C3.48412313,11.9429291 1.84033582,17.0539925 0.986753731,22.1289552 C0.123544776,27.2600746 -1.42108547e-14,32.8051493 -1.42108547e-14,37.7052239 L6.41791045,37.7052239 C6.41791045,32.8468657 6.54787313,27.7590672 7.31561567,23.1943284 C8.09298507,18.5734328 9.45759328,14.925653 11.5915485,12.597556 L6.86074627,8.26065299 Z"
                    id="Shape"
                  ></path>
                </g>
              </g>
            </g>
          </svg>
          <div class="custom-scanner"></div>
          <div class="app__help-text"></div>
        </div>
        <!-- 结果弹窗 -->
        <el-dialog title="解码结果" v-model:visible="visible" width="300px" center>
          <div class="result">
            {{ result }}
          </div>
          <div class="m-t-20">
            <el-button type="primary" @click="handleRawCode" plain
              >生成二维码</el-button
            >
            <el-button
              @click="handleCopy"
              plain
              :data-clipboard-text="result"
              class="tag-read"
              >复制</el-button
            >
          </div>
        </el-dialog>

        <!-- 右下角图标 -->
        <div class="app__switch-camera">
          <svg
            fill="#fff"
            t="1641799565969"
            class="icon"
            viewBox="0 0 1024 1024"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            p-id="1794"
            width="24"
            height="24"
          >
            <path
              d="M619.254 128a80 80 0 0 1 69.338 40.097l50.076 87.014H880c44.183 0 80 35.817 80 80V816c0 44.183-35.817 80-80 80H144c-44.183 0-80-35.817-80-80V335.11c0-44.182 35.817-80 80-80h139.122l51.525-87.651A80 80 0 0 1 403.613 128h215.641z m-271.32 304.312a8 8 0 0 0-11.003 1.625l-0.16 0.216-76.189 106.27a8 8 0 0 0 6.253 12.657l0.25 0.004h40.191l0.023 2.761C309.112 664.75 400.31 752.04 512 752.04c22.668 0 44.857-3.605 65.87-10.56 0.098-0.032 0.177-0.107 0.236-0.229 14.253-4.793 24.518-18.262 24.518-34.13 0-19.882-16.117-36-36-36-5.03 0-9.82 1.032-14.167 2.896-12.923 3.968-26.52 6.023-40.457 6.023-72.09 0-130.367-55.082-132.658-123.327l-0.052-2.072-0.014-1.556h40.183a8 8 0 0 0 6.656-12.44l-0.154-0.221-76.187-106.27a8 8 0 0 0-1.84-1.84zM512 353.04c-20.84 0-41.278 3.046-60.775 8.945a0.518 0.518 0 0 0-0.252 0.176c-14.941 4.382-25.852 18.192-25.852 34.55 0 19.882 16.118 36 36 36a35.9 35.9 0 0 0 12.928-2.392c12.172-3.482 24.913-5.28 37.951-5.28 72.09 0 130.367 55.083 132.658 123.328l0.052 2.072 0.014 1.578h-40.183l-0.25 0.004a8 8 0 0 0-6.441 12.382l0.189 0.276 76.187 106.27 0.161 0.216a8 8 0 0 0 12.618 0.082l0.225-0.299 76.188-106.27 0.153-0.221a8 8 0 0 0-1.778-10.78l-0.216-0.161-0.275-0.19a8 8 0 0 0-4.052-1.302l-0.334-0.007h-40.192l-0.023-2.784C714.888 440.328 623.69 353.04 512 353.04z"
              fill="#fff"
              p-id="1795"
            ></path>
          </svg>
        </div>

        <div class="app__select-photos">
          <svg
            fill="#fff"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <defs>
              <path id="a" d="M24 24H0V0h24v24z" />
            </defs>
            <clipPath id="b">
              <use xlink:href="#a" overflow="visible" />
            </clipPath>
            <path
              clip-path="url(#b)"
              d="M3 4V1h2v3h3v2H5v3H3V6H0V4h3zm3 6V7h3V4h7l1.83 2H21c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H5c-1.1 0-2-.9-2-2V10h3zm7 9c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-3.2-5c0 1.77 1.43 3.2 3.2 3.2s3.2-1.43 3.2-3.2-1.43-3.2-3.2-3.2-3.2 1.43-3.2 3.2z"
            />
          </svg>
        </div>
      </div>
    </el-tab-pane>
  </el-tabs>
</template>
<script>
import QRCode from "qrcodejs2";
import Clipboard from "clipboard";

export default {
  data() {
    return {
      activeName: "first",
      // 生码
      rawCode: "",
      qrcode: null,
      // 解码
      visible: false,
      result: "",
      clipboard: null
    };
  },
  methods: {
    handleClick() {
      if (!this.rawCode) {
        this.$message.error("请输入内容");
        return;
      }
      this.createCode();
    },
    // 生成二维码
    createCode() {
      if (this.qrcode) {
        this.$refs.qrCodeUrl.innerHTML = "";
      }
      this.qrcode = new QRCode(this.$refs.qrCodeUrl, {
        text: this.rawCode, // 需要转换为二维码的内容
        width: 100,
        height: 100,
        colorDark: "#000000",
        colorLight: "#ffffff",
        correctLevel: QRCode.CorrectLevel.H
      });
    },
    download() {
      if (!this.qrcode) {
        return;
      }
      let alink = document.createElement("a");
      //方法
      var img = document
        .getElementById("qrcode")
        .getElementsByTagName("img")[0];
      // 构建画布
      var canvas = document.createElement("canvas");
      canvas.width = img.width;
      canvas.height = img.height;
      canvas.getContext("2d").drawImage(img, 0, 0);
      // 构造url
      var url = canvas.toDataURL("image/png");
      alink.href = url;
      alink.download = "二维码"; //图片名
      alink.click();
    },
    handleResult() {
      this.visible = true;
      this.result = "我是结果";
    },
    // 生成二维码
    handleRawCode() {
      this.activeName = "first";
      this.visible = false;
      this.rawCode = this.result;
      this.createCode();
    },
    // 复制
    handleCopy() {
      this.clipboard = new Clipboard(".tag-read");
      this.clipboard.on("success", e => {
        this.$message.success("复制成功");
        e.clearSelection();
        // 释放内存
        this.clipboard.off("error");
        this.clipboard.off("success");
        this.clipboard.destroy();
      });
      this.clipboard.on("error", () => {
        this.$message.error("该浏览器不支持复制");
        // 释放内存
        this.clipboard.off("error");
        this.clipboard.off("success");
        this.clipboard.destroy();
      });
    }
  }
};
</script>
<style>
.tabs {
  margin: 0 auto;
  text-align: center;
  height: 100%;
  padding-top: 20px;
  box-sizing: border-box;
}
.el-tabs__header {
  width: 300px;
  margin: 0 auto !important;
}
.el-tab-pane {
  height: 100%;
}
.el-tabs__content {
  box-sizing: border-box;
  padding-top: 20px;
  height: calc(100% - 60px);
}
.raw-code {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.flex {
  display: flex;
}
.flex button {
  margin-left: 10px;
}
.qrcode {
  display: inline-block;
  margin: 20px 0;
}
.qrcode img {
  width: 132px;
  height: 132px;
  background-color: #fff;
  padding: 6px;
  box-sizing: border-box;
}
.download {
  margin-top: 20px;
  width: 100px;
}
.decoding {
  height: 100%;
}
.app__switch-camera {
  color: #fff;
  position: absolute;
  font-size: 18px;
  text-align: center;
  user-select: none;
  width: 58px;
  height: 58px;
  cursor: pointer;
  position: fixed;
  bottom: 100px;
  right: 20px;
  border-radius: 50%;
  background-color: #3f51b5;
  display: flex;
  align-items: center;
  justify-content: center;
}
.app__select-photos {
  width: 58px;
  height: 58px;
  cursor: pointer;
  position: fixed;
  bottom: 20px;
  right: 20px;
  border-radius: 50%;
  background-color: #3f51b5;
  display: flex;
  align-items: center;
  justify-content: center;
}
.app__overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  transition: all 200ms ease-in;
  width: 310px;
  height: 310px;
  margin: auto;
}
.result {
  background: rgb(247, 249, 247);
  padding: 12px 16px;
  border-radius: 2px;
  word-break: break-all;
}
.app__scanner-img {
  z-index: 1;
  position: relative;
  margin: 0 auto;
  display: block;
}
@-webkit-keyframes scanner {
  0% {
    bottom: 90%;
  }
  50% {
    bottom: 10%;
  }
  100% {
    bottom: 90%;
  }
}

@-moz-keyframes scanner {
  0% {
    bottom: 90%;
  }
  50% {
    bottom: 10%;
  }
  100% {
    bottom: 90%;
  }
}

@-o-keyframes scanner {
  0% {
    bottom: 90%;
  }
  50% {
    bottom: 10%;
  }
  100% {
    bottom: 90%;
  }
}

@keyframes scanner {
  0% {
    bottom: 90%;
  }
  50% {
    bottom: 10%;
  }
  100% {
    bottom: 90%;
  }
}

.custom-scanner {
  width: 220px;
  height: 2px;
  background: #4caf50;
  position: absolute;
  -webkit-transition: all 200ms linear;
  -moz-transition: all 200ms linear;
  transition: all 200ms linear;
  -webkit-animation: scanner 3s infinite linear;
  -moz-animation: scanner 3s infinite linear;
  -o-animation: scanner 3s infinite linear;
  animation: scanner 3s infinite linear;
  box-shadow: 0 1px 0 0 rgba(0, 0, 0, 0.4);
  display: block;
  left: 0px;
  right: 0;
  margin: auto;
}
video {
  top: 56px;
  left: 0;
  min-width: 100%;
  min-height: 100%;
  width: auto;
  height: auto;
  position: absolute;
}
.m-t-20 {
  margin-top: 20px;
}
</style>
