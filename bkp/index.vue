<template>
  <div id="__layout">
    <div>
          <nav class="navbar navbar-light bg-dark">
            <span class="navbar-brand mb-0 h1" style="color:#fff">Introduction to Nuxt.JS</span>
          </nav>
    <div class="container bg-light" style="margin-bottom:50px">
        <div align="center">
          <img src="https://2.bp.blogspot.com/-qF6r8Xp4LBI/XNgXQYwwB1I/AAAAAAAADDg/tXcyPILiTGYe-4z7G_2dzEX41uEqrGLGwCLcBGAs/s1600/Nuxt.png" alt=nuxt, width="60%">
        </div>
        <div class="blog-post">
            <h3>Nuxt.JSとは</h3>
            <p>Nuxt は、Vue の公式ガイドラインに沿って強力なアーキテクチャを提供するように設計されたフレームワークです。<br>一部分から徐々に採用することが可能で、静的なランディングページから複雑な企業向け web アプリケーションの作成に使用できます。</p>
            <br>
            <h3>主な機能</h3>
              <ul>
                <li>Vue ファイルで記述できること（*.vue）</li>
                <li>コードを自動的に分割すること</li>
                <li>サーバーサイドレンダリング</li>
                <li>非同期データをハンドリングするパワフルなルーティング</li>
              </ul>
            <br>
            <h3>実践編</h3>
            <p>習うより慣れろ。ということでさっそくgetを使ってTableを表示してみます。<br>
            例えば、以下のコードをscript側に記載することで外部のサイトからデータを取得し、hmtl側にレンダリングします。</p>
            <div class="code-block">
              <pre>
              <code>             
                async asyncData() {
                  const url = "https://jsonplaceholder.typicode.com/posts?_start=0&_limit=5"   
                  const {data} = await axios.get(url)
                    return{
                      items: data
                    }
                }       
              </code> 
              </pre>
            </div>
            <p>すると以下のようなコードが出力されるはずです</p> 
            <div class="container1">
                <table class="table table-striped table-hover">
                  <thead class="thead-dark">
                    <tr>
                      <th scope="col">userId</th>
                      <th scope="col">id</th>
                      <th scope="col">title</th>
                      <th scope="col">body</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(item, i) in items" :key="i">
                      <th scope="row">{{item.userId}}</th>
                      <td>{{item.id}}</td>
                      <td>{{item.title}}</td>
                      <td>{{item.body}}</td>
                    </tr>
                  </tbody>
                </table>
              </div>
          
              <h3>POSTを使ってみる</h3>
              <p>postの場合は以下のように記載します。　GETとPOSTの違いについてはこちらのサイトがおすすめです。</p>
              <a href="https://qiita.com/kanataxa/items/522efb74421255f0e0a1">GETとPOSTの違いについて</a>
              <div class="code-block">
                <pre>
                <code>             
                  async asyncData() {
                    const url = 'https://jsonplaceholder.typicode.com/posts?_start=0&_limit=0"'   
                    const perms = {
                      'userId': 1,
                      'id': 777
                      'title': 'postsuru'
                      'body': 'test desu'
                    }
                    const {data} = await axios.post(url, perms)
                      return{
                        items: data
                      }
                  }         
                </code> 
                </pre>
              </div>
                <p>すると以下のようなコードが出力されます。</p> 
            <div class="container2">
                <table class="table table-striped table-hover">
                  <thead class="thead-dark">
                    <tr>
                      <th scope="col">userId</th>
                      <th scope="col">id</th>
                      <th scope="col">title</th>
                      <th scope="col">body</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <th scope="row">1</th>
                      <td>1</td>
                      <td>sunt aut facere repellat provident occaecati excepturi optio reprehenderit</td>
                      <td>quia et suscipit suscipit recusandae consequuntur expedita et cum reprehenderit molestiae ut ut quas totam nos</td>
                    </tr>
                  </tbody>
                </table>
              </div>

             </div>   
            </div>
    </div>
  </div>
  
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      message: '', 
      } 
  }, 
  async asyncData(){
    const url = "https://jsonplaceholder.typicode.com/posts?_start=0&_limit=5"
    const {data} = await axios.get(url)
    console.log(data)
    return {
     items: data 
    } 
  }
}
</script>