<template>
    <form @submit.prevent="submitForm" class="booking-form">
        <div class="form-group">
            <label for="name"> Name</label>
            <input type="text" name="firstname" v-model="firstname" placeholder="First Name" required>
            <input type="text" name="lastname" v-model="lastname" placeholder="Last Name" required>
        </div>

        <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="email" placeholder="ex: myemail@email.com" required>
        </div>

        <div class="form-group">
            <label for="roomtype">Room type:</label>
            <select name="roomtype" v-model="roomtype" required>
                <option value="supreme">Supreme</option>
                <option value="king">King</option>
                <option value="cottage">Cottage</option>
            </select>
            <input id="roomprice" v-model="roomprice" readonly>
        </div>

        <div class="form-group">
            <label for="numberguest">Number of Guests:</label>
            <input type="button" class="btn btn-secondary btn-sm" id="decrease" value="decrease" @click="decrease(numberguest)">
            <input id="numberguest" v-model="numberguest" readonly>
            <input type="button" class="btn btn-secondary btn-sm" id="increase" value="increase" @click="increase(numberguest)">
        </div>

        <div class="form-group">
            <label for="arrivaldt">Arrival :</label>
            <input type="datetime-local" id="arrivaldt" v-model="arrivaldt" required>
        </div>

        <div class="form-group">
            <label for="departure">Departure :</label>
            <input type="datetime-local" id="departure" v-model="departure" required>
        </div>

        <div class="form-group">
            <label for="nights">Night :</label>
            <input id="nights" v-model="nights" readonly>
        </div>

        <div>
            <label for="totalprice">Total price : </label>
            <input type="text" id="totalprice" v-model="totalprice" readonly>
        </div>

        <div class="form-group">
            <label for="pickup" class="form-check-label">Free Pickup ?</label>
            <input type="radio" class="form-check-input" id="yes" v-model="pickup" value="Yes" required> 
            <label for="pickup" class="form-check-label"> Yes Please ! - Pick me up on arrival</label> <br>
              <input type="radio" class="form-check-input" id="no" v-model="pickup" value="No" required> 
              <label for="pickup" class="form-check-label"> No Thanks - I'll make my own way there</label> <br>
        </div>

        <div class="form-group">
            <label for="flightnumber"> Flight Number </label>
            <input type="text" name="flightnumber" v-model="flightnumber" required>
        </div>

        <div class="form-group">
            <label for="specialrequest"> Special Requests </label>
            <textarea name="specialrequest" cols="30" rows="10" v-model="specialrequest" required></textarea>
        </div>
            <!-- More form elements can be added here -->
        <button type="submit" class="btn btn-primary" >Submit</button>

        <div class="card text-center">
            <div class="card-body">
                <h5 class="card-title">Inclusion</h5>
                <p class="card-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Qui odit ipsa error quo repellendus. 
                        Minima, voluptatem doloribus molestias sit et, quia possimus maiores totam at, numquam quos vero reprehenderit architecto.</p>
            </div>
            <div class="card-body">
                <h5 class="card-title">Term and Condition</h5>
                <p class="card-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Qui odit ipsa error quo repellendus. 
                        Minima, voluptatem doloribus molestias sit et, quia possimus maiores totam at, numquam quos vero reprehenderit architecto.</p>
            </div>
        </div>
    </form>
        <p>Name : {{ firstname }} {{ lastname }}</p>
        <p>Email : {{ email }}</p>
        <p>Room type : {{ roomtype }}</p>
        <p>Number of guests: {{ numberguest }}</p>
        <p>Arrival : {{ arrivaldt }}</p>
        <p>Departure : {{ departure }}</p>
        <p>Nights : {{ nights }}</p>
        <p>Pickup : {{ pickup }}</p>
        <p>{{ flightnumber }}</p>
        <p>{{ specialrequest }}</p>
</template>

<script>
import { listRooms } from "../listRooms";
export default {
    data(){
        return{
            firstname: '',
            lastname: '',
            email: '',
            numberguest: 1,
            arrivaldt: '',
            departure: '',
            pickup: '',
            flightnumber: '',
            specialrequest: '',
            nights : 1,
            roomtype: 'supreme',
            roomprice : 1000,
            totalprice : 0  
        }
    },
    watch: {
        arrivaldt: 'countNights',
        departure: 'countNights',
        roomtype: 'countRoom',
        numberguest : 'countPrice',
        totalprice : 'countPrice'
    },
    methods:{
        increase(){
            this.numberguest++;
        },
        decrease(){
            this.numberguest--;
            if (this.numberguest<0) {
                this.numberguest=0;
            }
        },
        
        countNights(){
            if(this.arrivaldt && this.departure){
            // Parse input values into Date objects
            const arrivaldt = new Date(this.arrivaldt);
            const departure = new Date(this.departure); 

            // Calculate the time difference in milliseconds
            const timeDifference = departure - arrivaldt;

            // Convert milliseconds to days and set it to 'nights'
            this.nights = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
            } else {
                this.nights = null//
            }
        },
        
        countRoom(){
            switch (this.roomtype) {
                case 'supreme':
                    this.roomprice = 1000;
                    break;
                case 'king':
                    this.roomprice = 2000;
                    break;
                case 'cottage':
                    this.roomprice = 3000;
                    break;    
            
                default:
                    this.roomprice = 0;
            }
        },
        
        countPrice(){
            this.totalprice = this.numberguest  * this.nights * this.roomprice;
        }
    }
}
</script>

<style scoped>

</style>