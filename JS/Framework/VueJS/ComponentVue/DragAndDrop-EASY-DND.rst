<!-- drag -->
      <h4> add label </h4>
      <transition-group name="list" tag="div">
        <drag v-for="n in numbers" :key="n" class="label" :data="n" :type="typeof true" @cut="remove(n)">{{n}}</drag>
      </transition-group>
      <hr class="hr-80">
<!-- drag transition -->


<!-- drop -->
<drop class="copyLabel" @drop="onCopyDropLabel2" :accepts-data="(n) => n === n" accepts-type="boolean">
    <span v-for="(n, index2) in copied2" :key="index2">
        <transition-group name="list" tag="div">
            <drag v-for="n in numbers" :key="n" class="labels" :data="n" @cut="remove(n)">{{n}}
              <input class="node-left" v-model="nodeL" placeholder="node L">
              <input class="txt-label" v-model="message" placeholder="txt">
              <input class="node-right" v-model="nodeR" placeholder="node R">
            </drag>
        </transition-group>
    </span>
</drop>


<script>
  // @ is an alias to /src
import { Drag, Drop, DropMask } from "vue-easy-dnd";

  export default {
    name: 'Label',
    components: {
      Drag,
      Drop,
    },
    data: function(){
        return {
            APImessageGreeting: '',
            numbers: [""], // label uniq drag !important
            functions: ["function"], // function uniq drag !important
            copied: [], // label copied number
            copied1: [],
            copied2: [],
        }
    },
    methods: {
      onCopyDropLabel(e) {
        this.copied.push(e.data);
      },
      onCopyDropLabel1(e) {
        this.copied1.push(e.data);
      },
      onCopyDropLabel2(e) {
        this.copied2.push(e.data);
      },
      remove(n,n1) {
        let index = this.numbers.indexOf(n);
        this.numbers.splice(index, 1);

        let index1 = this.numbers1.indexOf(n1);
        this.numbers1.splice(index1, 1);

        let index2 = this.numbers2.indexOf(n);
        this.numbers2.splice(index2, 1);

        let function1 = this.functions.indexOf(f);
        this.functions.splice(function1, 1)
      }
    },
    created: async function(){
        const gResponse = await fetch("http://localhost:5000/greeting");
        const gObject = await gResponse.json();
        this.APImessageGreeting = gObject.greeting;
    }
  }
</script>
