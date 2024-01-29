<template>
  <div class="paginationTotalArea">
    <li class="btnBox">
      <button
        @click="changePage((currentPage = 1))"
        :class="{ disabled: currentPage === 1 }"
        class="btnPag"
      >
      {{ "|<==" }}

      </button>
      <button
        @click="changePage(currentPage - 1)"
        :class="{ disabled: currentPage === 1 }"
        class="btnPag"
      >
       {{ "<==" }}
      </button>

      <button
        @click="changePage(currentPage + 1)"
        :class="{ disabled: currentPage === totalPages }"
        class="btnPag"
      >
        ==>
      </button>
      <button
        @click="changePage((currentPage = totalPages))"
        :class="{ disabled: currentPage === totalPages }"
        class="btnPag"
      >
        ==>|
      </button>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    currentPage: Number,
    totalPages: Number
  },

  computed: {
    visiblePages() {
      const range = 2
      const startPage = Math.max(1, this.currentPage - range)
      const endPage = Math.min(this.totalPages, this.currentPage + range)

      const pages = []
      for (let i = startPage; i <= endPage; i++) {
        pages.push(i)
      }

      return pages
    }
  },

  methods: {
    changePage(newPage) {
      if (newPage >= 1 && newPage <= this.totalPages) {
        this.$emit('updatePage', newPage)
      }
    }
  }
}
</script>

<style scoped>
.paginationTotalArea {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
}

.btnBox {
  display: flex;
  gap: 2px;
}

.btnPag {
  position: relative;
  display: block;
  border-radius: 4px;
  text-transform: uppercase;
  background-color: transparent;
  color: #fff;
  font-size: 18px;
  overflow: hidden;
  transition: all 500ms ease;
  border: 2px solid #20e2d7;
  width: 80px;
  height: 40px;
  font-size: 10px;

  margin: 20px;
  z-index: 0;
  font-weight: 700;

  &::before {
    content: '';
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    margin: auto;
    background-color: #20e2d7;
    transition: all 500s ease;
    z-index: -1;
  }
}
.btnPag:hover {
  background-color: #20e2d7;
  color: #434343;
  cursor: pointer;
}

.disabled {
  display: none;
}

@media (min-width: 300px) and (max-width: 359px) {
  .btnPag {
    position: relative;
    display: block;
    border-radius: 4px;
    text-transform: uppercase;
    background-color: transparent;
    color: #fff;
    font-size: 18px;
    overflow: hidden;
    transition: all 500ms ease;
    border: 2px solid #20e2d7;
    width: 80px;
    height: 40px;
    font-size: 10px;
    margin-bottom: 20px;
    z-index: 0;
    font-weight: 700;
  }
}
</style>
