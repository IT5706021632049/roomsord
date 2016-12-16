<template>
  <div>
    <!-- ============================หน้าlogin================================== -->
    <div v-show="login" align="center">
    <div class="test">
      <h1 style="font-size: 30px;  font-family: 'Kanit', sans-serif;margin-top: 8%;margin-left: -1%;">ห้องโสตทัศนูปกรณ์</h1><br>
      <h1 style="font-size: 14px;  font-family: 'Kanit', sans-serif; margin-top: -2%;margin-left: -3%;">มหาวิทยาลัยพระจอมเกล้าพระนครเหนือ วิทยาเขต ปราจีนบุรี</h1><br>
    </div><br>
          <div style=
        "border: 2px solid red;
        width: 90%;
        height: 200px;
        margin-left: -5%;
        border-radius: 15px;">
      </div>
        <br>
        <h1 style="font-size: 20px;  font-family: 'Kanit', sans-serif;margin-top: -15%;margin-left: -5%;">เข้าสู่ระบบ</h1><br>
        <h3 style="=font-family: 'Kanit', sans-serif; font-size: 15px; font-weight: bold;margin-top: 1%;margin-left: -60%;">E-mail : &nbsp&nbsp</h3>
      <div>
        <input v-model="idlogin" class="label"  style=
        "width: 55%;
        border: 1px solid red;
        text-align: center;
        height: 35px;
        margin-left: 8%;
        margin-top: -2%;
        font-family: 'Kanit', sans-serif;
        font-size: 12px;
        border-radius: 5px;"
        placeholder="57060216XXXXXX@fitm.kmutnb.ac.th">
        <br>
        <h3 style="font-family: 'Kanit', sans-serif; font-size: 15px; font-weight: bold;margin-top: -1%;margin-left: -63%;">Password : &nbsp&nbsp</h3>
        <input  v-model="passlogin" class="label"  type="password" style=
        "width: 55%;
        border: 1px solid red;
        text-align: center;
        height: 35px;
        margin-left: 8%;
        margin-top: -2%;
        font-family: 'Kanit', sans-serif;
        font-size: 16px;
        border-radius: 5px;"
        placeholder="Password">
      </div><br>
        <button class="button is-danger" @click="checklogin()" style="
        width: 20%;
        height: 40px;
        font-size: 16px;
        font-weight: bold;
        margin-left: -2%;
        margin-top: -1%;
        font-family: 'Kanit', sans-serif;">
        ยืนยัน</button>
  </div>
<!-- ===============================หน้าเลือกรายการยืม====================== -->
<div v-show="checkloginpass">
  <div v-for="newIdStudents in IdStudent" style="margin-top: 5%;">
      <div style=""  v-show="newIdStudents.iduser === tempid && newIdStudents.passuser === temppass">
        <h1 align="center" style="font-size: 20px; font-weight: bold; font-family: 'Kanit', sans-serif;">เบิกอุปกรณ์ห้องโสตทัศนูปกรณ์</h1><br>
        <div align="center">
          <div class="button is-info is-outlined" style="font-family: 'Kanit', sans-serif;"> {{newIdStudents.iduser}}</div><button class="button is-danger" @click = "checklogout" style="font-family: 'Kanit', sans-serif;">ออกจากระบบ</button>
            <br><div v-for="newdate in IdStudent">
              <div style="font-family: 'Kanit', sans-serif; font-size: 18px;"  v-show="newdate.iduser === tempid && newdate.passuser === temppass">
              <br>วันที่ {{datenow}}
            </div>
            </div>
            <div>
            <h1 style="font-family: 'Kanit', sans-serif; font-size: 18px; margin-right: 50%;margin-top: 3%;">ชั้น
            <span class="select">
              <select @click="gfloor(selected)" v-model="selected">
                <option >B1-</option>
                <option >B2-</option>
                <option >B3-</option>
                <option >B4-</option>
              </select>
            </span></h1>
          </div>
          <div>
            <h1 style="font-family: 'Kanit', sans-serif; font-size: 18px; margin-left: 30%;  margin-top: -8%;">ห้องที่ใช้งาน
            <span class="select">
              <select @click="groomnumber(room)" v-model="room">
                <option>01</option>
                <option>02</option>
                <option>03</option>
                <option>04</option>
                <option>05</option>
                <option>06</option>
                <option>07</option>
                <option>08</option>
                <option>09</option>
                <option>10</option>
                <option>11</option>
                <option>12</option>
                <option>13</option>
                <option>14</option>
                <option>15</option>
                <option>16</option>
                <option>17</option>
                <option>18</option>
                <option>19</option>
                <option>20</option>
              </select>
            </span></h1>
          </div>
          <br>
              <h1 style="font-family: 'Kanit', sans-serif; font-size: 13px;">
        เวลา  <input type="radio" name="time"  @click="gtime(1)">09.00 - 12.00 น.
              <input type="radio" name="time"  @click="gtime(2)">13.00 - 16.00 น.
              <input type="radio" name="time"  @click="gtime(3)">17.00 - 20.00 น.
            <br><br></h1>
          </div>
          <!-- ===============================ไมค์สาย========================== -->
          <h1 style="font-family: 'Kanit', sans-serif;">
            <div style="
            border: 2px solid black;
            width: 90%;
            height: 400px;
            border-radius: 15px;
            background-color: #F0FFF0;
            margin-left: 5%;"><br>
<div v-for ="IdStudentuser in IdStudent" >
  <div v-show ="IdStudentuser.iduser === tempid" >
          <div style="margin-bottom: -1%; font-size: 14px; margin-left: 17%;">
              ไมค์สาย
              <input v-show="checkmikesai" @click="addEquipment(1)" type="button"  name="mikesai" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
              <input v-show="!checkmikesai" @click="removeEquipment(1)" type="button"  name="mikesai" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
            </div>

            <!-- ===============================ไมค์ลอย========================== -->

            <div style="margin-bottom: -1%; font-size: 14px; margin-top: -30px; margin-left: 65%;" >
                ไมค์ลอย
                <input v-show="checkmikeloy" @click="addEquipment(2)" type="button"  name="mikeloy" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                <input v-show="!checkmikeloy" @click="removeEquipment(2)" type="button"  name="mikeloy" value="ยกเลิก" class="button is-danger"style="font-family: 'Kanit', sans-serif; font-size: 14px;">
              </div>

              <!-- ===============================ไมค์สาย+ตู้ลำโพง========================== -->

              <div style="margin-bottom: -1%; font-size: 14px;  margin-left: 1%; margin-top: 8%;" >
                  ไมค์สาย+ตู้ลำโพง
                  <input v-show="checkmikesaispe" @click="addEquipment(3)" type="button"  name="mikesaispe" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                  <input v-show="!checkmikesaispe" @click="removeEquipment(3)" type="button"  name="mikesaispe" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                </div>

                <!-- ===============================ไมค์ลอย+ตู้ลำโพง========================== -->

                <div style="margin-bottom: -1%; font-size: 14px; margin-top: -9%; margin-left: 48%;" >
                    ไมค์ลอย+ตู้ลำโพง
                    <input v-show="checkmikeloyspe" @click="addEquipment(4)" type="button"  name="mikeloyspe" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                    <input v-show="!checkmikeloyspe" @click="removeEquipment(4)" type="button"  name="mikeloyspe" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                  </div>

                  <!-- ===============================ตู้ลำโพง========================== -->

                  <div style="margin-bottom: -1%; font-size: 14px; margin-top: 8%; margin-left: 16%;" >
                      ตู้ลำโพง
                      <input v-show="checkspeaker" @click="addEquipment(5)" type="button"  name="speaker" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                      <input v-show="!checkspeaker" @click="removeEquipment(5)" type="button"  name="speaker" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                    </div>

                    <!-- ===============================ปลั๊กไฟ========================== -->

                    <div style="margin-bottom: -1%; font-size: 14px; margin-top: -9%;margin-left: 67%;" >
                        ปลั๊กไฟ
                        <input v-show="checkplug" @click="addEquipment(6)" type="button"  name="plug" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                        <input v-show="!checkplug" @click="removeEquipment(6)" type="button"  name="plug" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                      </div>

                      <!-- ===============================โปรเจคเตอร์========================= -->

                      <div style="margin-bottom: -1%; font-size: 14px; margin-top: 8%; margin-left: 9%;" >
                          โปรเจคเตอร์
                          <input v-show="checkpro" @click="addEquipment(7)" type="button"  name="projecter" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                          <input v-show="!checkpro" @click="removeEquipment(7)" type="button"  name="projecter" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                        </div>

                        <!-- ===============================สายVGA + รีโมท========================= -->

                        <div style="margin-bottom: -1%; font-size: 14px; margin-top: -9%; margin-left: 53%;" >
                            สายVGA+รีโมท
                            <input v-show="checkvga" @click="addEquipment(8)" type="button"  name="vga" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                            <input v-show="!checkvga" @click="removeEquipment(8)" type="button"  name="vga" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                          </div>

                          <!-- ===============================สายสัญญาณเสียง========================= -->

                          <div style="margin-bottom: -1%; font-size: 14px; margin-top: 8%; margin-left: 1%;" >
                              สายสัญญาณเสียง
                              <input v-show="checksound" @click="addEquipment(9)" type="button"  name="sound" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                              <input v-show="!checksound" @click="removeEquipment(9)" type="button"  name="sound" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                            </div>

                            <!-- ===============================Visualizer========================= -->

                            <div style="margin-bottom: -1%; font-size: 14px; margin-top: -9%; margin-left: 61%;" >
                                Visualizer
                                <input v-show="checkvisua" @click="addEquipment(10)" type="button"  name="visua" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                                <input v-show="!checkvisua" @click="removeEquipment(10)" type="button"  name="visua" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                              </div>

                              <!-- ===============================Notebook========================= -->

                              <div style="margin-bottom: -1%; font-size: 14px; margin-top: 8%; margin-left: 13%;" >
                                  Notebook
                                  <input v-show="checknotebook" @click="addEquipment(11)" type="button"  name="notebook" value="เพิ่ม" class="button is-success" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                                  <input v-show="!checknotebook" @click="removeEquipment(11)" type="button"  name="notebook" value="ยกเลิก" class="button is-danger" style="font-family: 'Kanit', sans-serif; font-size: 14px;">
                                </div>

        <!-- ==============================ปุ่มยืนยัน - ออกจากระบบ========================== -->
          <br><br><button class="button is-primary" @click="getcode(IdStudentuser.id)" style="font-family: 'Kanit', sans-serif; font-size: 18px; margin-top: -6%; margin-left: 40%;" >ยืนยัน</button>
      </div>
    </div>
  </div>
  </h1>
  </div>
</div>
</div>
    <!-- ==============================แสดงอุปกรณืที่ยืม========================== -->
    <div v-show="tempid === 'admin' && adminpass === 'admin'" >
      <h1 style="
      font-size: 35px;
      font-weight: bold;
      font-family: 'Kanit', sans-serif;
      margin-right: 3%;" align="right">Administrator</h1><br>
      <h1 style="
      font-family: 'Kanit', sans-serif;
      font-size: 14px;
      margin-top: -2%;
      margin-right: 5%;" align="right" >ห้องโสตทัศนูปกรณ์ มหาวิทยาลัยพระจอมเกล้าพระนครเหนือ วิทยาเขต ปราจีนบุรี</h1>
      <button @click = "showhistory()" class="button is-warning" style="font-family: 'Kanit', sans-serif; margin-left: 35%;margin-top: 2%;" >ดูประวัติการยืม-คืน</button>
      <button  @click = "checklogout()" class="button is-danger" style="font-family: 'Kanit', sans-serif;  margin-left: 70%; font-size: 14px; margin-top: -9%;">ออกจากระบบ</button>
      <hr style="width: 80%; background-color: orange;" >
      <div style="margin-left: 5%;">
        <u> <h1 style="font-family: 'Kanit', sans-serif;font-size: 14px;">เพิ่ม E-mail รหัสนักศึกษาเข้าระบบ<br><br></u>
          <h1 style="font-family: 'Kanit', sans-serif;font-size: 14px;">E-mail :</h1>
          <div style="margin-top: -6%; margin-left: 15%;"><input v-model="newIdStudent.iduser" style="
          width: 80%;
          border: 1px solid red;
          text-align: center;
          height: 25px;
          font-family: 'Kanit', sans-serif;
          font-size: 14px;"
          placeholder="57060216XXXXXX@fitm.kmutnb.ac.th"></div>
          <h1 style="font-family: 'Kanit', sans-serif;font-size: 14px; margin-top: 2%; margin-left: -4%;">Password : </h1>
          <div style="margin-top: -6%; margin-left: 15%;"><input v-model="newIdStudent.passuser" style="
          width: 80%;
          border: 1px solid red;
          text-align: center;
          height: 25px;
          font-family: 'Kanit', sans-serif;
          font-size: 14px;"
          placeholder="Password"></div>
          </h1>
          <button @click = "addUser()" class="button is-warning" style="font-family: 'Kanit', sans-serif; margin-left: 20%;margin-top: 4%;" >เพิ่มรหัสนักศึกษา</button>
    </div>
    <hr style="width: 80%; background-color: orange;" >
    <div style="margin-left: 5%;">
      <u><h2 style="font-family: 'Kanit', sans-serif;font-size: 14px;">รายการเบิกอุปกรณ์</h2></u><br>
      <h2 style="font-family: 'Kanit', sans-serif;font-size: 12px; ">ผู้ยืม</h2>
      <div v-for ="sh in IdStudent" >
        <div v-show="sh.status === true " style="font-family: 'Kanit', sans-serif;font-size: 12px; ">
          {{sh.iduser}}
          <br>ห้อง {{sh.floor}}
          {{sh.roomnumber}}&nbsp;&nbsp;&nbsp;&nbsp;
        เวลายืม  {{sh.time}}&nbsp;&nbsp;
          วันที่{{sh.date}}<br>
        <button @click="showlist2(sh.id)" class="button is-success" style="font-family: 'Kanit', sans-serif;">รายการที่ยืม</button>
          <button @click="test(sh.id, sh.iduser, sh.floor, sh.roomnumber, sh.time, sh.date, sh.MicrophoneSai, sh.MicrophoneLoy, sh.MikeSaiSpe, sh.MikeLoySpe, sh.Notebook, sh.Plug, sh.Projecter, sh.Sound, sh.Speaker, sh.Vga, sh.Visualizer )" class="button is-warning" style="font-family: 'Kanit', sans-serif;">คืน&ลบรายการ</button>
              <br>
            </div>
          </div>
        </div>
</div>
    <!-- ===============================Admin หน้ารายการยืม========================== -->
<div v-show="shistory">
<button  @click="backadmin()">กลับ</button>
<div v-for ="showhistory in history">
    {{showhistory.iduser}}
    {{showhistory.floor}}
    {{showhistory.roomnumber}}
    {{showhistory.time}}
    {{showhistory.date}}
    {{showhistory.trun}}
    {{showhistory.list}}
  </div>
</div>
    <!-- ==================================================================== -->
</div>
</template>
<script>
/* global swal */
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyCxBZhCT21Sxj_kGzRHCy0P1z-ePcvTu-g',
  authDomain: 'roomsord.firebaseapp.com',
  databaseURL: 'https://roomsord.firebaseio.com',
  storageBucket: 'roomsord.appspot.com',
  messagingSenderId: '614964738386'
}
firebase.initializeApp(config)
var IdStudent = firebase.database().ref('IdStudent')
var history = firebase.database().ref('history')
export default {
  mounted () {
    let vm = this
    IdStudent.on('child_added', function (snapshot) {
      var ids = snapshot.val()
      ids.id = snapshot.key
      vm.IdStudent.push(ids)
    })
    history.on('child_added', function (snapshot) {
      var idh = snapshot.val()
      idh.id = snapshot.key
      vm.history.push(idh)
    })
    history.on('child_changed', function (snapshot) {
      var idr = snapshot.key
      var find = vm.history.find(history => history.id === idr)
      find.iduser = snapshot.val().iduser
      find.floor = snapshot.val().floor
      find.roomnumber = snapshot.val().roomnumber
      find.time = snapshot.val().time
      find.date = snapshot.val().date
      find.trun = snapshot.val().trun
      find.list = snapshot.val().list
    })
    IdStudent.on('child_removed', function (snapshot) {
      var idr = snapshot.key
      vm.IdStudent.splice(vm.IdStudent.findIndex(IdStudent => IdStudent.id === idr), 1)
    })
    IdStudent.on('child_changed', function (snapshot) {
      var idr = snapshot.key
      var find = vm.IdStudent.find(IdStudent => IdStudent.id === idr)
      find.MicrophoneLoy = snapshot.val().MicrophoneLoy
      find.MicrophoneSai = snapshot.val().MicrophoneSai
      find.MikeSaiSpe = snapshot.val().MikeSaiSpe
      find.MikeLoySpe = snapshot.val().MikeLoySpe
      find.Speaker = snapshot.val().Speaker
      find.Plug = snapshot.val().Plug
      find.Projecter = snapshot.val().Projecter
      find.Vga = snapshot.val().Vga
      find.Sound = snapshot.val().Sound
      find.Visualizer = snapshot.val().Visualizer
      find.Notebook = snapshot.val().Notebook
      find.time = snapshot.val().time
      find.floor = snapshot.val().floor
      find.roomnumber = snapshot.val().roomnumber
      find.status = snapshot.val().status
      if (vm.newIdStudent === idr) {
        vm.newIdStudent.MicrophoneLoy = snapshot.val().MicrophoneLoy
        vm.newIdStudent.MicrophoneSai = snapshot.val().MicrophoneSai
        vm.newIdStudent.MikeSaiSpe = snapshot.val().MikeSaiSpe
        vm.newIdStudent.MikeLoySpe = snapshot.val().MikeLoySpe
        vm.newIdStudent.Speaker = snapshot.val().Speaker
        vm.newIdStudent.Plug = snapshot.val().Plug
        vm.newIdStudent.Projecter = snapshot.val().Projecter
        vm.newIdStudent.Vga = snapshot.val().Vga
        vm.newIdStudent.Sound = snapshot.val().Sound
        vm.newIdStudent.Visualizer = snapshot.val().Visualizer
        vm.newIdStudent.Notebook = snapshot.val().Notebook
        vm.newIdStudent.time = snapshot.val().time
        vm.newIdStudent.floor = snapshot.val().floor
        vm.newIdStudent.roomnumber = snapshot.val().roomnumber
        vm.newIdStudent.status = snapshot.val().status
      }
    })
  },
  data () {
    return {
      checkloginpass: false,
      shistory: false,
      adminpass: '',
      selected: '',
      room: '',
      tempid: '',
      temppass: '',
      idlogin: '',
      passlogin: '',
      login: true,
      logout: true,
      checkmikesai: true,
      checkmikeloy: true,
      checkmikesaispe: true,
      checkmikeloyspe: true,
      checkspeaker: true,
      checkplug: true,
      checkpro: true,
      checkvga: true,
      checksound: true,
      checkvisua: true,
      checknotebook: true,
      checktime: true,
      checkroomnumber: true,
      gettime: '',
      getroomnumber: '',
      getfloor: '',
      shlist: '',
      back: '',
      list1: '',
      list2: '',
      list3: '',
      listtotal: '',
      datenow: '',
      history: [],
      newHistory: {
        iduser: '',
        floor: '',
        roomnumber: '',
        time: '',
        date: '',
        trun: '',
        list: ''
      },
      IdStudent: [],
      newIdStudent: {
        iduser: '',
        passuser: '',
        MicrophoneSai: '',
        MicrophoneLoy: '',
        MikeSaiSpe: '',
        MikeLoySpe: '',
        Speaker: '',
        Plug: '',
        Projecter: '',
        Vga: '',
        Sound: '',
        Visualizer: '',
        Notebook: '',
        time: '',
        roomnumber: '',
        floor: '',
        status: false
      },
      timetest: ''
    }
  },
  methods: {
    checklogin () {
      this.tempid = this.idlogin
      this.temppass = this.passlogin
      this.checkloginpass = true
      var today = new Date()
      var date = today.getDate() + '/' + (today.getMonth() + 1) + '/' + today.getFullYear()
      this.datenow = date
      if (this.tempid === 'admin') {
        this.adminpass = this.passlogin
      }
      if (this.checkloginpass === true) {
        this.login = false
      }
    },
    checklogout () {
      this.login = true
      this.tempid = ''
      this.checkmikesai = true
      this.checkmikeloy = true
      this.checkmikesaispe = true
      this.checkmikeloyspe = true
      this.checkspeaker = true
      this.checkplug = true
      this.checkpro = true
      this.checkvga = true
      this.checksound = true
      this.checkvisua = true
      this.checknotebook = true
      this.gettime = ''
      this.selected = ''
      this.room = ''
      this.shlist = ''
      this.idlogin = ''
      this.passlogin = ''
    },
    addUser () {
      let result = IdStudent.push(this.newIdStudent)
      this.newIdStudent.id = result.key
      this.newIdStudent.iduser = ''
      this.newIdStudent.passuser = ''
    },
    getcode (id) {
      this.list1 = this.newIdStudent.MicrophoneSai + this.newIdStudent.MicrophoneLoy + this.newIdStudent.MikeSaiSpe + this.newIdStudent.MikeLoySpe + this.newIdStudent.Speaker + this.newIdStudent.Plug + this.newIdStudent.Projecter + this.newIdStudent.Vga + this.newIdStudent.Sound + this.newIdStudent.Visualizer + this.newIdStudent.Notebook
      this.list2 = this.getfloor + this.getroomnumber + '/' + this.gettime
      this.listtotal = this.list2 + ' ' + this.list1
      swal({
        title: 'QR Code',
        text: 'อุปกรณ์ที่ยืม,กด OK ออกจากระบบอัตโนมัติ',
        imageUrl: 'https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=' + this.listtotal + '',
        imageWidth: 200,
        imageHeight: 100,
        animation: false
      }).then(function () {
        swal('เรียบร้อย', 'ออกจากระบบอัตโนมัติ', 'success')
      })
      this.login = true
      this.checkloginpass = false
      this.login = true
      this.tempid = ''
      this.checkmikesai = true
      this.checkmikeloy = true
      this.checkmikesaispe = true
      this.checkmikeloyspe = true
      this.checkspeaker = true
      this.checkplug = true
      this.checkpro = true
      this.checkvga = true
      this.checksound = true
      this.checkvisua = true
      this.checknotebook = true
      this.gettime = ''
      this.selected = ''
      this.room = ''
      this.shlist = ''
      this.idlogin = ''
      this.passlogin = ''
      var vm = this
      var today = new Date()
      var date = today.getDate() + '/' + (today.getMonth() + 1) + '/' + today.getFullYear()
      firebase.database().ref('IdStudent/' + id).update({
        MicrophoneSai: vm.newIdStudent.MicrophoneSai = this.newIdStudent.MicrophoneSai,
        MicrophoneLoy: vm.newIdStudent.MicrophoneLoy = this.newIdStudent.MicrophoneLoy,
        MikeSaiSpe: vm.newIdStudent.MikeSaiSpe = this.newIdStudent.MikeSaiSpe,
        MikeLoySpe: vm.newIdStudent.MikeLoySpe = this.newIdStudent.MikeLoySpe,
        Speaker: vm.newIdStudent.Speaker = this.newIdStudent.Speaker,
        Plug: vm.newIdStudent.Plug = this.newIdStudent.Plug,
        Projecter: vm.newIdStudent.Projecter = this.newIdStudent.Projecter,
        Vga: vm.newIdStudent.Vga = this.newIdStudent.Vga,
        Sound: vm.newIdStudent.Sound = this.newIdStudent.Sound,
        Visualizer: vm.newIdStudent.Visualizer = this.newIdStudent.Visualizer,
        Notebook: vm.newIdStudent.Notebook = this.newIdStudent.Notebook,
        time: vm.newIdStudent.time = this.gettime,
        floor: vm.newIdStudent.floor = this.getfloor,
        roomnumber: vm.newIdStudent.roomnumber = this.getroomnumber,
        status: vm.newIdStudent.status = true,
        date: date
      })
      this.newIdStudent.MicrophoneSai = ''
      this.newIdStudent.MicrophoneLoy = ''
      this.newIdStudent.MikeSaiSpe = ''
      this.newIdStudent.MikeLoySpe = ''
      this.newIdStudent.Speaker = ''
      this.newIdStudent.Plug = ''
      this.newIdStudent.Projecter = ''
      this.newIdStudent.Vga = ''
      this.newIdStudent.Sound = ''
      this.newIdStudent.Visualizer = ''
      this.newIdStudent.Notebook = ''
      this.gettime = ''
      this.getfloor = ''
      this.getroomnumber = ''
    },
    removelist (id) {
      var vm = this
      firebase.database().ref('IdStudent/' + id).update({
        MicrophoneSai: vm.newIdStudent.MicrophoneSai = '',
        MicrophoneLoy: vm.newIdStudent.MicrophoneLoy = '',
        MikeSaiSpe: vm.newIdStudent.MikeSaiSpe = '',
        MikeLoySpe: vm.newIdStudent.MikeLoySpe = '',
        Speaker: vm.newIdStudent.Speaker = '',
        Plug: vm.newIdStudent.Plug = '',
        Projecter: vm.newIdStudent.Projecter = '',
        Vga: vm.newIdStudent.Vga = '',
        Sound: vm.newIdStudent.Sound = '',
        Visualizer: vm.newIdStudent.Visualizer = '',
        Notebook: vm.newIdStudent.Notebook = '',
        time: vm.newIdStudent.time = '',
        floor: vm.newIdStudent.floor = '',
        roomnumber: vm.newIdStudent.roomnumber = '',
        status: vm.newIdStudent.status = false
      })
    },
    addHistory (id, iduser, floor, roomnumber, time, date, timetrun, mloy, msai, mls, mss, nb, pg, pjt, sd, sk, vga, vslz) {
      this.newHistory.iduser = iduser
      this.newHistory.floor = floor
      this.newHistory.roomnumber = roomnumber
      this.newHistory.time = time
      this.newHistory.date = date
      this.newHistory.trun = timetrun
      this.newHistory.list = mloy + msai + mls + mss + nb + pg + pjt + sd + sk + vga + vslz
      let result = history.push(this.newHistory)
      this.newHistory.id = result.key
    },
    showhistory () {
      this.shistory = true
      this.tempid = ''
    },
    showlist2 (id) {
      var student = this.IdStudent.find(student => student.id === id)
      this.list1 = '' + student.MicrophoneSai + student.MicrophoneLoy + student.MikeSaiSpe + student.MikeLoySpe + student.Speaker + student.Plug + student.Projecter + student.Vga + student.Sound + student.Visualizer + student.Notebook
      swal(this.list1)
    },
    test (id, iduser, floor, roomnumber, time, date, mloy, msai, mls, mss, nb, pg, pjt, sd, sk, vga, vslz) {
      var vm = this
      swal({
        title: 'ต้องการคืนและลบข้อมูล',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'คืน&ลบข้อมูล'
      }).then(function (e) {
        vm.removelist(id)
        vm.timeretrun(id, iduser, floor, roomnumber, time, date, mloy, msai, mls, mss, nb, pg, pjt, sd, sk, vga, vslz)
        swal(
          'ลบข้อมูลเรียบร้อยแล้ว',
          'success'
        )
      })
    },
    timeretrun (id, iduser, floor, roomnumber, time, date, mloy, msai, mls, mss, nb, pg, pjt, sd, sk, vga, vslz) {
      var vm = this
      var today = new Date()
      var timetrun = today.getHours() + '.' + today.getMinutes()
      console.log(timetrun)
      firebase.database().ref('IdStudent/' + id).update({
        timetrun: timetrun
      })
      vm.addHistory(id, iduser, floor, roomnumber, time, date, timetrun, mloy, msai, mls, mss, nb, pg, pjt, sd, sk, vga, vslz)
    },
    backadmin () {
      this.tempid = 'admin'
      this.shlist = ''
      this.shistory = false
    },
    gtime (num) {
      if (num === 1) {
        this.gettime = '09.00 - 12.00'
        console.log(this.gettime)
      }
      if (num === 2) {
        this.gettime = '13.00 - 16.00'
        console.log(this.gettime)
      }
      if (num === 3) {
        this.gettime = '17.00 - 20.00'
        console.log(this.gettime)
      }
    },
    gfloor (selected) {
      if (selected === 'B1-') {
        this.getfloor = 'B1-'
        console.log(this.getfloor)
      }
      if (selected === 'B2-') {
        this.getfloor = 'B2-'
        console.log(this.getfloor)
      }
      if (selected === 'B3-') {
        this.getfloor = 'B3-'
        console.log(this.getfloor)
      }
      if (selected === 'B4-') {
        this.getfloor = 'B4-'
        console.log(this.getfloor)
      }
    },
    groomnumber (room) {
      if (room === '01') {
        this.getroomnumber = '01'
        console.log(this.getroomnumber)
      }
      if (room === '02') {
        this.getroomnumber = '02'
        console.log(this.getroomnumber)
      }
      if (room === '03') {
        this.getroomnumber = '03'
        console.log(this.getroomnumber)
      }
      if (room === '04') {
        this.getroomnumber = '04'
        console.log(this.getroomnumber)
      }
      if (room === '05') {
        this.getroomnumber = '05'
        console.log(this.getroomnumber)
      }
      if (room === '06') {
        this.getroomnumber = '06'
        console.log(this.getroomnumber)
      }
      if (room === '07') {
        this.getroomnumber = '07'
        console.log(this.getroomnumber)
      }
      if (room === '08') {
        this.getroomnumber = '08'
        console.log(this.getroomnumber)
      }
      if (room === '09') {
        this.getroomnumber = '09'
        console.log(this.getroomnumber)
      }
      if (room === '10') {
        this.getroomnumber = '10'
        console.log(this.getroomnumber)
      }
      if (room === '11') {
        this.getroomnumber = '11'
        console.log(this.getroomnumber)
      }
      if (room === '12') {
        this.getroomnumber = '12'
        console.log(this.getroomnumber)
      }
      if (room === '13') {
        this.getroomnumber = '13'
        console.log(this.getroomnumber)
      }
      if (room === '14') {
        this.getroomnumber = '14'
        console.log(this.getroomnumber)
      }
      if (room === '15') {
        this.getroomnumber = '15'
        console.log(this.getroomnumber)
      }
      if (room === '16') {
        this.getroomnumber = '16'
        console.log(this.getroomnumber)
      }
      if (room === '17') {
        this.getroomnumber = '17'
        console.log(this.getroomnumber)
      }
      if (room === '18') {
        this.getroomnumber = '18'
        console.log(this.getroomnumber)
      }
      if (room === '19') {
        this.getroomnumber = '19'
        console.log(this.getroomnumber)
      }
      if (room === '20') {
        this.getroomnumber = '20'
        console.log(this.getroomnumber)
      }
    },
    removeEquipment (num, id) {
      if (num === 1) {
        this.newIdStudent.MicrophoneSai = ''
        var vm = this
        firebase.database().ref('IdStudent/' + id).update({
          MicrophoneSai: vm.newIdStudent.MicrophoneSai = this.newIdStudent.MicrophoneSai
        })
        this.checkmikesai = true
        console.log(this.newIdStudent.MicrophoneSai)
      }
      if (num === 2) {
        this.newIdStudent.MicrophoneLoy = ''
        this.checkmikeloy = true
        console.log(this.newIdStudent.MicrophoneLoy)
      }
      if (num === 3) {
        this.newIdStudent.MikeSaiSpe = ''
        this.checkmikesaispe = true
        console.log(this.newIdStudent.MikeSaiSpe)
      }
      if (num === 4) {
        this.newIdStudent.MikeLoySpe = ''
        this.checkmikeloyspe = true
        console.log(this.newIdStudent.MikeLoySpe)
      }
      if (num === 5) {
        this.newIdStudent.Speaker = ''
        this.checkspeaker = true
        console.log(this.newIdStudent.Speaker)
      }
      if (num === 6) {
        this.newIdStudent.Plug = ''
        this.checkplug = true
        console.log(this.newIdStudent.Plug)
      }
      if (num === 7) {
        this.newIdStudent.Projecter = ''
        this.checkpro = true
        console.log(this.newIdStudent.Projecter)
      }
      if (num === 8) {
        this.newIdStudent.Vga = ''
        this.checkvga = true
        console.log(this.newIdStudent.Vga)
      }
      if (num === 9) {
        this.newIdStudent.Sound = ''
        this.checksound = true
        console.log(this.newIdStudent.Sound)
      }
      if (num === 10) {
        this.newIdStudent.Visualizer = ''
        this.checkvisua = true
        console.log(this.newIdStudent.Visualizer)
      }
      if (num === 11) {
        this.newIdStudent.Notebook = ''
        this.checknotebook = true
        console.log(this.newIdStudent.Notebook)
      }
    },
    addEquipment (num, id) {
      if (num === 1) {
        this.newIdStudent.MicrophoneSai = 'ไมค์สาย,'
        this.checkmikesai = false
        console.log(this.newIdStudent.MicrophoneSai)
      }
      if (num === 2) {
        this.newIdStudent.MicrophoneLoy = 'ไมค์ลอย,'
        this.checkmikeloy = false
        console.log(this.newIdStudent.MicrophoneLoy)
      }
      if (num === 3) {
        this.newIdStudent.MikeSaiSpe = 'ไมค์สาย + ตู้ลำโพง,'
        this.checkmikesaispe = false
        console.log(this.newIdStudent.MikeSaiSpe)
      }
      if (num === 4) {
        this.newIdStudent.MikeLoySpe = 'ไมค์ลอย + ตู้ลำโพง,'
        this.checkmikeloyspe = false
        console.log(this.newIdStudent.MikeLoySpe)
      }
      if (num === 5) {
        this.newIdStudent.Speaker = 'ตู้ลำโพง,'
        this.checkspeaker = false
        console.log(this.newIdStudent.Speaker)
      }
      if (num === 6) {
        this.newIdStudent.Plug = 'ปลั๊กไฟ,'
        this.checkplug = false
        console.log(this.newIdStudent.Plug)
      }
      if (num === 7) {
        this.newIdStudent.Projecter = 'โปรเจคเตอร,์'
        this.checkpro = false
        console.log(this.newIdStudent.Projecter)
      }
      if (num === 8) {
        this.newIdStudent.Vga = 'สายVGA + รีโมท,'
        this.checkvga = false
        console.log(this.newIdStudent.Vga)
      }
      if (num === 9) {
        this.newIdStudent.Sound = 'สายสัญญาณเสียง,'
        this.checksound = false
        console.log(this.newIdStudent.Sound)
      }
      if (num === 10) {
        this.newIdStudent.Visualizer = 'Visualizer,'
        this.checkvisua = false
        console.log(this.newIdStudent.Visualizer)
      }
      if (num === 11) {
        this.newIdStudent.Notebook = 'Notebook,'
        this.checknotebook = false
        console.log(this.newIdStudent.Notebook)
      }
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Kanit');
</style>
