<script setup>
import { ref, computed } from "vue";
const props = defineProps(["month", "dir", "count"]);

const imageList = ref(
  Array.from({ length: props.count }, (x, idx) => {
    return {
      idx: idx,
      url: `./src/assets/images/${props.dir}/${idx + 1}.jpeg`,
    };
  })
);
const selectedNo = ref(0);

const selectImage = (idx) => {
  selectedNo.value = idx;
};

const thumbnailList = computed(() => {
  if (imageList.value.length == 0) return [];
  if (imageList.value.length < 5)
    return imageList.value.map(({ url, idx }) => {
      return { url, idx };
    });

  if (selectedNo.value < 2)
    return imageList.value.slice(0, 5).map(({ url, idx }) => {
      return { url, idx };
    });
  if (selectedNo.value + 1 > imageList.value.length)
    return imageList.value.slice(imageList.value.length - 5, imageList.value.length).map(({ url, idx }) => {
      return { url, idx };
    });
  return imageList.value.slice(selectedNo.value - 2, selectedNo.value + 3).map(({ url, idx }) => {
    return { url, idx };
  });
});
</script>

<template>
  <div class="monthly-card-container">
    <h1 class="main-title">{{ month }}</h1>
    <img
      v-if="imageList.length > 0"
      :key="image"
      class="selected-image"
      :src="`./src/assets/images/${dir}/${selectedNo + 1}.jpeg`"
    />
    <div class="image-list">
      <div class="thumbnail-list">
        <div class="thumbnail-container" v-for="thumbnail in thumbnailList" :key="thumbnail.idx">
          <img
            class="thumbnail"
            :class="thumbnail.idx === selectedNo ? 'selected' : ''"
            :src="thumbnail.url"
            @click="selectImage(thumbnail.idx)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main-title {
  text-align: center;
  margin-bottom: 24px;
  font-family: "SDSamliphopangche_Outline" !important;
}
.monthly-card-container {
  display: flex;
  width: 100%;
  flex-direction: column;
}
.selected {
  box-sizing: border-box;
  border: 2px white solid;
  border-radius: 2px;
}
.image-list {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: flex-start;
  margin-top: 30px;
  margin-bottom: 60px;
}

.thumbnail-list {
  display: flex;
  flex-grow: 1;
  justify-content: flex-start;
}
.playlist-btn {
  font-size: 24px;
  font-weight: bold;
  height: 100%;
  cursor: pointer;
  color: var(--grey);
}
.playlist-btn:hover {
  color: white;
}

.selected-image {
  width: 100%;
  aspect-ratio: 16/9;
  height: auto;
  object-fit: contain;
}
.next-btn {
  margin-left: auto;
}

.thumbnail-container {
  position: relative;
  width: 18%;
  padding-bottom: 13.5%;
  margin: 0 1%;
}
.thumbnail {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: contain;
  cursor: pointer;
}

.gallery-btn-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 24px;
}

.gallery-btn-wrapper {
  width: 100%;
  display: flex;
  flex-direction: row;
  margin-top: 12px;
}

.gallery-btn {
  width: 64px;
  height: 32px;
  text-align: center;
  line-height: 32px;
  box-sizing: border-box;
  border-radius: 4px;
  opacity: 0.8;
  cursor: pointer;
}

.gallery-delete-btn {
  background-color: var(--red);
  margin-left: 12px;
}

.gallery-update-btn {
  background-color: var(--green);
}

.gallery-btn:hover {
  opacity: 1;
}
</style>
