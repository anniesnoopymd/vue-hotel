<template>
    <div class="room_container" data-toggle="modal" data-target="#detailModal" @click="sendData()">
        <div class="cover" :style="bg_css">
            <h6>{{room_data.name}}</h6><i class="i fa fa-times" @click="del_room(id)"></i>
        </div>
        <div class="info">
            <div class="room_eng">{{room_data.eng}}</div><span class="icon"><span v-if="room_data.equipment.breakfast"><i class="i fa fa-coffee"></i></span><span v-if="room_data.equipment.bathtub"><i class="i fa fa-bath"></i></span><span v-if="room_data.equipment.wifi"><i class="i fa fa-wifi"></i></span></span>
            <div class="show_dis">{{room_data.discount}} * {{hotel_discount}} = {{discount_show}} discount</div>
            <s>TWD ${{room_data.price}}</s>
            <div class="red_text">TWD ${{price_final_show}}</div>
        </div>

        <!-- Modal -->
        <div class="modal fade" id="detailModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="detailModal">Room details</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <div class="cover" :style="bg_css">
                            <h6>{{room_data.name}}</h6><i class="i fa fa-times" @click="del_room(id)"></i>
                        </div>
                        <div>
                            <div class="room_eng">{{room_data.eng}}</div><span class="icon"><span v-if="room_data.equipment.breakfast"><i class="i fa fa-coffee"></i></span><span v-if="room_data.equipment.bathtub"><i class="i fa fa-bath"></i></span><span v-if="room_data.equipment.wifi"><i class="i fa fa-wifi"></i></span></span>
                            <div class="show_dis">{{room_data.discount}} * {{hotel_discount}} = {{discount_show}} discount</div>
                            <s>TWD ${{room_data.price}}</s>
                            <div class="red_text">TWD ${{price_final_show}}</div>
                        </div>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                        <button type="button" class="btn btn-primary">Save changes</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
    name: 'RoomList',
    props:["room_data","hotel_discount","id","del_room","service_fee"],
    computed:{
        discount_show(){
            return parseInt(this.room_data.discount*this.hotel_discount*100)
        },
        discount_final(){
            return parseInt(this.room_data.discount*this.hotel_discount*this.room_data.price)
        },
        price_final_show(){
            return parseInt(this.discount_final)+parseInt(this.service_fee)
        },
        bg_css(){
            return {
                "background-image":"url('"+this.room_data.cover+"')"
            }
        }
    },
    methods:{
        sendData(item){
            console.log(item)

        }
    }
}
</script>

<style scoped>
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
</style>
