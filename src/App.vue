<template>
  <div id="app">
    <div class="container">
      <h1 style="text-align: center;">抽卡统计</h1>
      <div>
        <input type="text" class="form-control" placeholder="母猪名" v-model='username' @keydown='userInputFunction'/>
        <br>
        <input type="text" class="form-control" placeholder="决斗编号" v-model='pknum' @keydown='pkInputFunction'/>
      </div>
      <div>
        <h3>{{username}}的抽卡记录</h3>
        <h4>总览</h4>
        <table class="table table-striped">
          <thead>
            <tr>
              <th>总计</th>
              <th v-for="item in rareList">{{item}}</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>{{resultlist.oversee.all}}</td>
              <td>{{resultlist.oversee.iron}}({{Math.round(resultlist.oversee.iron / resultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{resultlist.oversee.bronze}}({{Math.round(resultlist.oversee.bronze / resultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{resultlist.oversee.sliver}}({{Math.round(resultlist.oversee.sliver / resultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{resultlist.oversee.gold}}({{Math.round(resultlist.oversee.gold / resultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{resultlist.oversee.platinum}}({{Math.round(resultlist.oversee.platinum / resultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{resultlist.oversee.black}}({{Math.round(resultlist.oversee.black / resultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
            </tr>
          </tbody>
        </table>
        <h4>详细</h4>
        <table class="table table-striped">
          <thead>
            <tr>
              <th>#</th>
              <th>时间</th>
              <th>卡池类型</th>
              <th>结果</th>
              <th>稀有度</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item,index) in resultlist.detail">
              <td>{{index+1}}</td>
              <td>{{item.time}}</td>
              <td>{{item.type}}</td>
              <td>{{item.card.name}}</td>
              <td>{{rareList[item.card.rare]}}</td>
            </tr>
          </tbody>
        </table>
        <br>
        <br>
        <h3>决斗记录 with No.{{pknum}}</h3>
        <h4>总览</h4>
        <table class="table table-striped">
          <thead>
            <tr>
              <th>总计</th>
              <th v-for="item in rareList">{{item}}</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>{{eventresultlist.oversee.all}}</td>
              <td>{{eventresultlist.oversee.iron}}({{Math.round(eventresultlist.oversee.iron / eventresultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{eventresultlist.oversee.bronze}}({{Math.round(eventresultlist.oversee.bronze / eventresultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{eventresultlist.oversee.sliver}}({{Math.round(eventresultlist.oversee.sliver / eventresultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{eventresultlist.oversee.gold}}({{Math.round(eventresultlist.oversee.gold / eventresultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{eventresultlist.oversee.platinum}}({{Math.round(eventresultlist.oversee.platinum / eventresultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
              <td>{{eventresultlist.oversee.black}}({{Math.round(eventresultlist.oversee.black / eventresultlist.oversee.all * 10000) / 100.00 + "%"}})</td>
            </tr>
          </tbody>
        </table>
        <h4>详细</h4>
        <table class="table">
          <tbody>
            <tr v-for="(item,key) in eventresultlist.detail">
              <td>{{key}}</td>
              <td>
                <table class="table table-striped">
                  <thead>
                    <tr>
                      <th>总计</th>
                      <th v-for="item in rareList">{{item}}</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td>{{item.oversee.all}}</td>
                      <td>{{item.oversee.iron}}({{Math.round(item.oversee.iron / item.oversee.all * 10000) / 100.00 + "%"}})</td>
                      <td>{{item.oversee.bronze}}({{Math.round(item.oversee.bronze / item.oversee.all * 10000) / 100.00 + "%"}})</td>
                      <td>{{item.oversee.sliver}}({{Math.round(item.oversee.sliver / item.oversee.all * 10000) / 100.00 + "%"}})</td>
                      <td>{{item.oversee.gold}}({{Math.round(item.oversee.gold / item.oversee.all * 10000) / 100.00 + "%"}})</td>
                      <td>{{item.oversee.platinum}}({{Math.round(item.oversee.platinum / item.oversee.all * 10000) / 100.00 + "%"}})</td>
                      <td>{{item.oversee.black}}({{Math.round(item.oversee.black / item.oversee.all * 10000) / 100.00 + "%"}})</td>
                    </tr>
                  </tbody>
                </table>
                <table class="table table-striped">
                  <thead>
                    <tr>
                      <th>#</th>
                      <th>时间</th>
                      <th>卡池类型</th>
                      <th>结果</th>
                      <th>稀有度</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(value,index) in item.detail">
                      <td>{{index+1}}</td>
                      <td>{{value.time}}</td>
                      <td>{{value.type}}</td>
                      <td>{{value.card.name}}</td>
                      <td>{{rareList[value.card.rare]}}</td>
                    </tr>
                  </tbody>
                </table>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import Hello from './components/Hello'
import $ from 'jquery'
export default {
  name: 'app',
  components: {
    Hello
  },
  data: function () {
    return {
      resultlist: {
        oversee: {
          all: 0,
          iron: 0,
          bronze: 0,
          sliver: 0,
          gold: 0,
          platinum: 0,
          black: 0
        },
        detail: []
      },
      eventresultlist: {
        oversee: {},
        detail: {}
      },
      rareList: ['铁', '铜', '银', '金', '白', '黑'],
      rareNameList: ['iron', 'bronze', 'sliver', 'gold', 'platinum', 'black'],
      pknum: '',
      username: ''
    }
  },
  methods: {
    userInputFunction: function (e) {
      if (e.keyCode !== 13) return
      if (this.username === '') return
      // 通知socket服务器换房间
      this.$socket.emit('join-user', this.username)
      $.ajax({
        url: 'http://127.0.0.1:9980/record/' + this.username,
        type: 'GET',
        dataType: 'json',
        success: (data) => {
          this.resultlist.detail = data
          // 统计
          for (let i in this.resultlist.oversee) {
            this.resultlist.oversee[i] = 0
          }
          data.forEach((item, index) => {
            if (this.resultlist.oversee[this.rareNameList[item.card.rare]] === undefined) this.resultlist.oversee[this.rareNameList[item.card.rare]] = 0
            this.resultlist.oversee[this.rareNameList[item.card.rare]]++
          })
          this.resultlist.oversee.all = data.length
        }
      })
    },
    pkInputFunction: function (e) {
      if (e.keyCode !== 13) return
      if (this.pknum === '') return
      this.$socket.emit('join-event', this.pknum)
      $.ajax({
        url: 'http://127.0.0.1:9980/record/event/' + this.pknum,
        type: 'GET',
        dataType: 'json',
        success: (data) => {
          // 计算总计
          for (let i in this.rareNameList) {
            this.eventresultlist.oversee[this.rareNameList[i]] = 0
          }
          this.eventresultlist.oversee.all = data.length
          // 按人头分类
          let obj = {}
          data.forEach((value, index) => {
            if (obj[value.user] === undefined) {
              obj[value.user] = {
                detail: [],
                oversee: {
                  all: 0,
                  iron: 0,
                  bronze: 0,
                  sliver: 0,
                  gold: 0,
                  platinum: 0,
                  black: 0
                }
              }
            }
            this.eventresultlist.oversee[this.rareNameList[value.card.rare]]++
            obj[value.user].oversee[this.rareNameList[value.card.rare]]++
            obj[value.user].oversee.all++
            obj[value.user].detail.push(value)
          })
          this.eventresultlist.detail = obj
        }
      })
    }
  },
  sockets: {
    connect: function () {
      console.log('socket connected')
    },
    newRecord: function (arg) {
      this.resultlist.oversee[this.rareNameList[arg.card.rare]]++
      this.resultlist.oversee.all++
      this.resultlist.detail.push(arg)
    },
    newEventRecord: function (arg) {
      this.eventresultlist.oversee[this.rareNameList[arg.card.rare]]++
      this.eventresultlist.oversee.all++
      let user = this.eventresultlist.detail[arg.user]
      // 当user不存在的时候 初始化
      if (user === undefined) {
        this.eventresultlist.detail.$set(arg.user, {
          oversee: {
            all: 0,
            iron: 0,
            bronze: 0,
            sliver: 0,
            gold: 0,
            platinum: 0,
            black: 0
          },
          detail: []
        })
        user = this.eventresultlist.detail[arg.user]
      }
      user.oversee[this.rareNameList[arg.card.rare]]++
      user.oversee.all++
      user.detail.push(arg)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
