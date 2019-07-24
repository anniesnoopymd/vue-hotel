<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-3 left_block">
          <h4>Room Detail</h4>
          <hr/>
          <label>Discount</label>
          <input class="form-control" v-model="discount"/>
          <label>Service fee</label>
          <input class="form-control" v-model="service_fee"/>
          <button class="addroom_btn" @click="add_room">Add room</button>
          <hr/>
          <h6>Edit room</h6>
          <select class="form-control dropdown" v-model="edit_id">
            <option v-for="(item,index) in rooms" :key="index" :value="index">{{item.name}}</option>
          </select>
          <div class="edit_room" v-for="(room,id) in [rooms[edit_id]]">
            <h6>{{room.name}}</h6>
            <label>Room name</label>
            <input class="form-control" v-model="room.name"/>
            <label>English name</label>
            <input class="form-control" v-model="room.eng"/>
            <label>Price</label>
            <input class="form-control" v-model="room.price"/>
            <label>Discount</label>
            <input class="form-control" v-model="room.discount"/>
            <label>房間設備:
              <input class="checkbox-custom" type="checkbox" v-model="room.equipment.breakfast"/>
              <label class="checkbox-custom-label">Breakfast</label>
              <input class="checkbox-custom" type="checkbox" v-model="room.equipment.bathtub"/>
              <label class="checkbox-custom-label">Bathtub</label>
              <input class="checkbox-custom" type="checkbox" v-model="room.equipment.wifi"/>
              <label class="checkbox-custom-label">Wifi</label>
            </label>
          </div>
        </div>
        <div class="col-sm-9 right_block">
          <h4>Room list</h4>
          <hr/>
          <div class="row">
            <div class="col-sm-4 col_room" v-for="(room,id) in rooms">
              <room-list :room_data="room" :hotel_discount="discount" :id="id" :del_room="del_room" :service_fee="service_fee"></room-list>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <RoomList></RoomList>
</template>


<script>
import HelloWorld from './components/HelloWorld.vue'
import RoomList from './components/RoomList.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    RoomList
  },
  data(){
    return{
      rooms: [
        {
          "name": "經濟雙人房",
          "eng": "Economy Double Room",
          "price": 7000,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room%20(1).jpg",
          "discount": 0.9,
          "equipment": {
            "wifi": false,
            "bathtub": true,
            "breakfast": true
          }
        },
        {
          "name": "海景三人房",
          "eng": "Sea view triple Room",
          "price": 7800,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room%20(2).jpg",
          "discount": 0.8,
          "equipment": {
            "wifi": true,
            "bathtub": true,
            "breakfast": false
          }
        },
        {
          "name": "典雅景觀房",
          "eng": "Elegant landscape Room",
          "price": 5400,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room%20(3).jpg",
          "discount": 0.85,
          "equipment": {
            "wifi": false,
            "bathtub": true,
            "breakfast": true
          }
        },
        {
          "name": "尊享豪華房",
          "eng": "Exclusive Deluxe Room",
          "price": 9800,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room%20(4).jpg",
          "discount": 0.8,
          "equipment": {
            "wifi": true,
            "bathtub": false,
            "breakfast": true
          }
        },
        {
          "name": "商務雙人房",
          "eng": "Business Double Room",
          "price": 5600,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room (5).jpg",
          "discount": 0.9,
          "equipment": {
            "wifi": true,
            "bathtub": false,
            "breakfast": false
          }
        },
        {
          "name": "溫泉雙人房",
          "eng": "Hot spring double Room",
          "price": 8400,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room (6).jpg",
          "discount": 0.6,
          "equipment": {
            "wifi": true,
            "bathtub": true,
            "breakfast": true
          }
        },
        {
          "name": "總統套房",
          "eng": "Presidential Suite",
          "price": 23000,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room (7).jpg",
          "discount": 0.75,
          "equipment": {
            "wifi": true,
            "bathtub": true,
            "breakfast": true
          }
        },
        {
          "name": "奢華四人房",
          "eng": "Luxury four Room",
          "price": 8500,
          "amount": 0,
          "cover": "http://bosscode.monoame.com/20170323_vue_comp/img/room (8).jpg",
          "discount": 0.7,
          "equipment": {
            "wifi": true,
            "bathtub": true,
            "breakfast": false
          }
        }
      ],
      discount: 0.9,
      service_fee: 200,
      edit_id: 0
    }
  },
  methods:{
    add_room(){
      let new_room = {
        "name": "新房間",
        "eng": "New Room",
        "price": 5000,
        "amount": 0,
        "cover": "",
        "discount": 0.5,
        "equipment": {
          "wifi": false,
          "bathtub": true,
          "breakfast": true
        }
      }
      this.rooms.push(new_room)
    },
    del_room(id){
      this.rooms.splice(id,1)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.container-fluid {
  margin: 20px;
}

.left_block {
  background-color: #7189bf;
  padding: 22px;
  color: #fff;
  height: 95vh;
  overflow-y: scroll;
}
.left_block label {
  font-size: 15px;
}

.right_block {
  border: 2px solid #7189bf;
  padding: 20px 30px;
  height: 95vh;
  overflow-y: scroll;
}

.addroom_btn {
  margin: 10px 0px 10px 0px;
  border-radius: 5px;
  padding: 5px 15px;
  font-size: 13px;
  color: #fff;
  font-family: Microsoft Jhenghei;
  border: 1px solid #DEDEDE;
  background-color: #7189bf;
  cursor: pointer;
  transition-duration: 0.3s;
}
.addroom_btn::before {
  content: "+ ";
}
.addroom_btn:hover {
  background-color: #fff;
  color: #7189bf;
}

.room_container {
  margin: 10px 0px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
  transition-duration: 0.5s;
}
.room_container:hover {
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.7);
}
.room_container .cover {
  height: 170px;
  background-color: #eee;
  position: relative;
  background-size: cover;
  background-position: center center;
}
.room_container .cover h6 {
  background-color: #000;
  color: #fff;
  opacity: 0.7;
  padding: 5px 15px;
  position: absolute;
  bottom: 5px;
  font-size: 17px;
}

.block {
  width: 70px;
  height: 5px;
  background-color: #614ad3;
  margin-top: -10px;
}

.fa-times {
  position: absolute;
  color: #fff;
  top: 5px;
  right: 5px;
  cursor: pointer;
  transition-duration: 0.3s;
}
.fa-times:hover {
  color: #DB4343;
}

.form-control {
  height: 35px;
  font-size: 14px;
  padding-left: 10px;
}

s {
  font-size: 14px;
  margin-top: 15px;
  padding: 10px;
}

.red_text {
  background-color: #DB4343;
  color: #fff;
  width: 120px;
  font-size: 16px;
  padding: 2px 10px;
}

.show_dis {
  font-size: 14px;
  padding: 0px 0px 10px 10px;
}

.info {
  padding-top: 10px;
}
.info .room_eng {
  font-size: 14px;
  margin-left: 10px;
  font-weight: 700;
}
.info .icon {
  padding-left: 10px;
}
.info i {
  color: #BDBDBC;
  font-size: 14px;
  padding: 2px;
}

.edit_room {
  margin-top: 10px;
  padding: 10px;
  font-size: 14px;
  background-color: #6377a5;
}
.edit_room label {
  margin: 15px 0px 5px 0px;
}

.dropdown {
  font-family: Microsoft Jhenghei;
}

::-webkit-scrollbar {
  width: 5px;
}

::-webkit-scrollbar-thumb {
  -webkit-border-radius: 10px;
  background: #4D4D4C;
}

</style>
