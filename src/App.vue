<script>
// import elementUI from 'element-plus';
export default {
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      placeholder: "请输入搜索内容(项目已经开源，直接输入github即可)"
    }
  }
}

document.addEventListener("DOMContentLoaded", function () {
  // console.log("DOM加载完毕");
  const input = document.getElementById("searchInput"); // 获取输入框
  // const logo = document.getElementsByTagName("img");
  // 按下键盘上某一个键👇
  document.addEventListener("keydown", function (event) {
    const inputValue = input.value; // 获取输入框的值

    const google = inputValue.match(/gg\s+(.+)/); // 匹配输入框的值
    const baidu = inputValue.match(/bd\s+(.+)/);
    const github = inputValue.match(/gt\s+(.+)/);
    const bing = inputValue.match(/bing\s+(.+)/);
    const yandex = inputValue.match(/yd\s+(.+)/);
    if (event.key === "Enter") { // 按下回车
      if (inputValue == "github") {
        window.open("https://github.com/MCheping8108/49team-search")
        return;
      }

      if (google && google[1].trim() !== "") { // 匹配成功
        window.open("https://www.google.com/search?q=" + google[1].trim()) // 跳转到Google搜索
        return;
      }
      if (baidu && baidu[1].trim() !== "") {
        window.open("https://www.baidu.com/s?wd=" + baidu[1].trim()) // 跳转到百度搜索
        return;
      }

      if (github && github[1].trim() !== "") {
        window.open("https://github.com/search?q=" + github[1].trim()) // 跳转到Github搜索
        return;
      }

      if (bing && bing[1].trim() !== "") {
        window.open("https://cn.bing.com/search?q=" + bing[1].trim()) // 跳转到Bing搜索
        return;
      }

      if (yandex && yandex[1].trim() !== "") {
        window.open("https://yandex.com/search/?text=" + yandex[1].trim()) // 跳转到Yandex搜索
        return;
      }
      else {
        // if (!isElseExecuted) {
        //   isElseExecuted = true;

        //   const error = document.getElementById("error");
        //   const warning = document.createElement("li");
        //   const br = document.createElement("br");
        //   // warning.innerHTML = '<el-alert title="⚠ERROR⚠: 没有匹配到任何搜索引擎" type="error" />';
        //   error.appendChild(br);
        //   warning.textContent = "⚠ERROR⚠: 没有匹配到任何搜索引擎";
        //   error.appendChild(warning);
        //   return;
        // }
        const error = document.getElementById("error");
        const warning = document.createElement("li");
        const br = document.createElement("br");
        // warning.innerHTML = '<el-alert title="⚠ERROR⚠: 没有匹配到任何搜索引擎" type="error" />';
        error.appendChild(br);
        warning.textContent = "⚠ERROR⚠: 没有匹配到任何搜索引擎";
        error.appendChild(warning);
        return;
        
      }
    }
  });
})

</script>

<template>
  <div class="images">
    <img src="https://mcheping520.gitee.io/graphic-bed/image/EH2vkuQABsNiwKg.png" alt="">
  </div>
  <div id="search">
    <input type="text" id="searchInput" :placeholder="placeholder">
  </div>
  <div id="error">

  </div>
</template>

<style>
body {
  background-color: #202124;
}

.images {
  text-align: center;
}

.images img {
  width: 100px;
  height: 100px;
  /* border-radius: 50px; */
  margin-top: 50px;
  margin-bottom: 50px;
}

#search {
  text-align: center;
}

#search input {
  transition: 0.5s;
  color: #eee;
  border-radius: 20px;
  border: none;
  background-color: #404246;
  text-align: center;
  width: 500px;
  height: 50px;
}

#search input:focus {
  outline: none;
}

#search input:hover {
  transform: 0.5s;
  background-color: #4c4d4f;
}

#error {
  color: red;
  text-align: center;
}

@media screen and (max-width: 768px) {
  #app input {
    width: 100%;
    height: 500;
  }
}
</style>
