<script setup>
import { ref } from 'vue';
import { marked } from 'marked';

marked.setOptions({
  breaks: true,  // 改行を有効にする
  gfm: true,     // GitHub Flavored Markdownを使用
});

// Markdown入力を保持する変数
const markdownContent = ref('');

// プレビュー用のHTMLを保持する変数
const preview = ref('');

// 入力されたMarkdownをHTMLに変換してプレビューを更新
const updatePreview = () => {
  preview.value = marked(markdownContent.value); // MarkdownをHTMLに変換
  console.log(preview.value)
};
</script>

<template>
    <div class="container">
      <div class="preview" v-html="preview"></div>
      <div class="editor">
        <textarea
          v-model="markdownContent"
          @input="updatePreview"
          class="editor"
          placeholder="Enter your markdown here..."
        ></textarea>
      </div>
    </div>
</template>

<style>
  * {
    box-sizing: border-box;
  }
  
  .container {
    display: flex;
    flex-direction: column; /* 縦方向に並べる */
    width: 90vw; /* 横幅を100vwにする */
    height: 90vh; /* 高さを100vhにする */
    justify-content: center; /* 縦方向に中央揃え */
    align-items: center; /* 横方向に中央揃え */
    margin: 0 auto; /* 横方向の余白を追加 */
  }
  
  .editor, .preview {
    width: 80%; /* 横方向の中央に配置 */
  }
  
  .editor {
    height: 30%; /* エディタの高さを30%に設定 */
  }
  
  .editor textarea {
    width: 100%;
    height: 100%;
    font-family: "Arial", sans-serif;
    border: 1px solid #ccc;
    resize: none;
    padding: 10px;
  }
  
  .preview {
    height: 70%; /* プレビューの高さを70%に設定 */
    background-color: #bfeed8;
    overflow-y: auto;
    padding: 10px;
    text-align: left;
  }
  
  .preview table {
    width: 100%;
    border-collapse: collapse;
    border-color: 3px solid red !important;
  }
  
  .preview th {
    color: red !important; /* ヘッダー文字の色を赤に設定 */
    background-color: #f1f1f1;
    text-align: center;
    padding: 10px;
  }
  
  
  
</style>