## Card

card コンテナに情報を統合する

### 基本的な使い方

card はタイトル、内容、操作を含む。

:::demo card は `header` と `body` からなる。ヘッダはオプションであり、その内容の分布はスロットの名前に依存します。

```html
<el-card class="box-card">
  <template #header>
    <div class="card-header">
      <span>Card name</span>
      <el-button class="button" type="text">Operation button</el-button>
    </div>
  </template>
  <div v-for="o in 4" :key="o" class="text item">{{'List item ' + o }}</div>
</el-card>

<style>
  .card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .box-card {
    width: 480px;
  }
</style>
```

:::

### シンプルな card

ヘッダー部分は省略可能です。

:::demo

```html
<el-card class="box-card">
  <div v-for="o in 4" :key="o" class="text item">{{'List item ' + o }}</div>
</el-card>

<style>
  .text {
    font-size: 14px;
  }

  .item {
    padding: 18px 0;
  }

  .box-card {
    width: 480px;
  }
</style>
```

:::

### 画像付き

設定を追加することで、よりリッチなコンテンツを表示することができます。

:::demo `body-style` 属性は、カスタム `body` の CSS スタイルを定義します。この例ではレイアウトにも `el-col` を用いています。

```html
<el-row>
  <el-col
    :span="8"
    v-for="(o, index) in 2"
    :key="o"
    :offset="index > 0 ? 2 : 0"
  >
    <el-card :body-style="{ padding: '0px' }">
      <img
        src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png"
        class="image"
      />
      <div style="padding: 14px;">
        <span>Yummy hamburger</span>
        <div class="bottom">
          <time class="time">{{ currentDate }}</time>
          <el-button type="text" class="button">Operating</el-button>
        </div>
      </div>
    </el-card>
  </el-col>
</el-row>

<style>
  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .button {
    padding: 0;
    min-height: auto;
  }

  .image {
    width: 100%;
    display: block;
  }
</style>

<script>
  export default {
    data() {
      return {
        currentDate: new Date(),
      }
    },
  }
</script>
<!--
<setup>

  import { defineComponent, ref } from 'vue';

  export default defineComponent({
    setup() {
      const currentDate = ref(new Date());

      return {
        currentDate,
      };
    },
  });

</setup>
-->
```

:::

### シャドウ

card のシャドウを表示するタイミングを定義することができます。

:::demo `shadow` 属性は、card の影をいつ表示するかを決定します。`always`, `hover`, `never` のいずれかです。

```html
<el-row :gutter="12">
  <el-col :span="8">
    <el-card shadow="always"> Always </el-card>
  </el-col>
  <el-col :span="8">
    <el-card shadow="hover"> Hover </el-card>
  </el-col>
  <el-col :span="8">
    <el-card shadow="never"> Never </el-card>
  </el-col>
</el-row>
```

:::

### Attributes

| Attribute  | Description                                                              | Type   | Accepted Values        | Default             |
| ---------- | ------------------------------------------------------------------------ | ------ | ---------------------- | ------------------- |
| header     | card のタイトルを指定します。`slot#header` で渡された DOM も受け付ける。 | string | —                      | —                   |
| body-style | ボディの CSS スタイル                                                    | object | —                      | { padding: '20px' } |
| shadow     | card の影を表示するタイミング                                            | string | always / hover / never | always              |
