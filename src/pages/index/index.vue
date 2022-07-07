<template>
  <view>
    <div class="mainbox">
      <div class="oldDay">
        <div class="title">一年前</div>
        <div class="time">2021/07/01</div>
        <div class="content">在我年轻的时候，曾以为金钱是世界上最重要的东西，现在我老了，才知道的确如此。</div>
      </div>
      <div class="lineBox" v-for="(item, index) in list" :key="index">
        <nut-row>
          <nut-col :span="4">
            <div class="dayBox">
              <div class="day">12</div>
              <div class="month">5月/周五</div>
            </div>
          </nut-col>
          <nut-col :span="20">
            <div class="cardBox">{{ item.title }}</div>
          </nut-col>
        </nut-row>
      </div>
    </div>
  </view>
</template>

<script>
import { ref, reactive, onMounted, toRefs } from "vue";
import { fetchList } from "./api.js";
import "./index.scss";

export default {
  setup() {
    const msg = ref("Hello world");
    const state = reactive({
      list: [{ title: "22222" }],
      msg: "111111",
    });

    onMounted(() => {
      getList();
    });

    const getList = () => {
      fetchList().then((res) => {
        console.log("res", res.todoList);
        state.list = res.doneList;
      });
    };

    return {
      ...toRefs(state),
      getList,
    };
  },
};
</script>
