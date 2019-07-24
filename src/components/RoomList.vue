<template>
    <div class="room_container">
        <div class="cover" :style="bg_css">
            <h6>{{room_data.name}}</h6><i class="i fa fa-times" @click="del_room(id)"></i>
        </div>
        <div class="info">
            <div class="room_eng">{{room_data.eng}}</div><span class="icon"><span v-if="room_data.equipment.breakfast"><i class="i fa fa-coffee"></i></span><span v-if="room_data.equipment.bathtub"><i class="i fa fa-bath"></i></span><span v-if="room_data.equipment.wifi"><i class="i fa fa-wifi"></i></span></span>
            <div class="show_dis">{{room_data.discount}} * {{hotel_discount}} = {{discount_show}} discount</div>
            <s>TWD ${{room_data.price}}</s>
            <div class="red_text">TWD ${{price_final_show}}</div>
        </div>
    </div>
</template>

<script>
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
    }
}
</script>

<style scoped>

</style>
