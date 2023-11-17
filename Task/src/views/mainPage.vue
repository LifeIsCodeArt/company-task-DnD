<script setup>
  import {ref} from "vue";
  import MenuItems from "../components/menuItems.vue";
  import draggable from 'vuedraggable'
  const menuItems = ref([
    {
      text: 'Операции',
      imagePath: '../src/components/icons/operation-icon.svg',
    },
    {
      text: 'Отчеты',
      imagePath: '../src/components/icons/reports-icon.svg',
    },
    {
      text: 'Контрагенты',
      imagePath: '../src/components/icons/contragents-icon.svg',
    },
    {
      text: 'Проекты',
      imagePath: '../src/components/icons/work-icon.png',
    }, {
      text: 'Статьи расходов',
      imagePath: '../src/components/icons/accounts-icon.svg',
    },
    {
      text: 'Сотрудники',
      imagePath: '../src/components/icons/person-icon.svg',
    }
  ])
  
    const  list1 = ref([
          { id: 1, name: "ИП Бирюков Михаил Алексеевич", bank:'monobank', reason:'Выплаты', recipient:'Сайт Volkswagen', profit:true,
            moneyChange:'+21 239 ₴', status: true, description:'Оплата за продвижение \n' +
                'Google Adwords июнь-июль'},
          { id: 2, name: "Роман Мельников", bank:'monobank', reason:'Зарплата сотрудникам', recipient:'ИП Eltron',  profit: false,
            moneyChange:'-56 000 ₴', status: false, description:'Аванс Июль'},
          { id: 3, name: "ООО «Кранкомплект»", bank:'monobank', reason:'Разработка', recipient:'Сайт Кранкомплект', profit: true,
            moneyChange:'+170 000 ₴', status: true, description:'Аванс за разработку'}
        ])
    const  list2 = ref([
          { id: 5, name: "Роман Мельников", bank:'monobank', reason:'Расходы на офис', recipient:'Обучение сотрудников', profit:false,
            moneyChange:'-8 000 ₴', status: true, description:'Оплата обучения'},
          { id: 6, name: "ООО «Кранкомплект»", bank:'monobank', reason:'Разработка', recipient:'Сайт Кранкомплект', profit:true,
            moneyChange:'+170 000 ₴', status: true, description:'Аванс за разработку'},
          { id: 7, name: "ИП Бирюков Михаил Алексеевич", bank:'monobank', reason:'Продвижение', recipient:'Сайт Volkswagen', profit:true,
            moneyChange:'+21 239 ₴', status: true, description:'Оплата за продвижение \n' +
                'Google Adwords июнь-июль'}
        ])


  const add = function() {
        this.list.value.push({ name: "Juan" });
      }

  const replace = function() {
        this.list.value = [{ name: "Edgard" }];
      }

  let clone = function(el) {
        return {
          name: el.name + "cloned"
        };
      }

  const log = function(evt) {
        window.console.log(evt);
      }

  const activeSection = ref(1)
</script>

<template>
  <div class="w-[1440px] flex h-full mx-auto py-[26px] px-[36px] border-2 border-gray-900 relative">
      <div class="">
          <div class="flex">
              <div class="flex">
                  <button class="flex justify-center items-center w-[44px] h-[44px] border-2 rounded-xl">
                      <img src="../components/icons/chevron-left-svgrepo-com.svg" height="15px" width="15px" alt="" class="">
                  </button>
                  <button class="flex justify-center items-center w-[94px] h-[44px] border-2 rounded-xl mx-[4px]">
                      <img src="../components/icons/calendar-icon.svg" height="15px" width="15px" alt="" class="">
                      <p class="ml-[10px] font-semibold">Июль</p>
                  </button>
                  <button class="flex justify-center items-center w-[44px] h-[44px] border-2 rounded-xl">
                      <img src="../components/icons/chevron-right-svgrepo-com.svg" height="15px" width="15px" alt="" class="font-bold">
                  </button>
              </div>
            <div class="ml-[16px] mr-[51px] flex">
                <input type="text" class="w-[400px] px-[16px] py-[13px] h-[44px] border-2 rounded-xl outline-none"
                         placeholder="Поиск по проекту, контрагенту или счёту">
            </div>
            <div class="w-[384px] h-[44px] rounded-xl flex items-center bg-[#EEEEEE]">
                <div class="w-[120px] h-full flex items-center justify-center bg-white rounded-xl border outline-none">
                    <button class=" flex items-center filter outline-none ">Фильтр</button>
                </div>
                <div class="w-[198px] h-[30px] flex">
                    <div class="image relative flex ml-[15px]">
                        <img src="../components/images/bg.png"  width="30" height="30" class="w-[30px] h-[30px]">
                    </div>
                    <div class="ml-[7px] image relative flex">
                        <img src="../components/images/bg-2.png"  width="30" height="30" class="w-[30px] h-[30px]">
                    </div>
                    <div class="ml-[7px] image relative flex">
                        <img src="../components/images/bg-3.png"  width="30" height="30" class="w-[30px] h-[30px]">
                    </div>
                    <div class="ml-[7px] image relative flex">
                        <img src="../components/images/bg-4.png" width="30" height="30" class="w-[30px] h-[30px]">
                    </div>
                    <div class="ml-[7px] flex">
                        <img src="../components/images/add-profile.png" width="30" height="30" class="w-[30px] h-[30px]">
                    </div>
                </div>
            </div>
         </div>
            <div class="mt-[26px] mb-[36px]">
                <img src="../components/images/money-move.jpg" alt="" class="">
            </div>
            <div class="flex justify-between">
                <div class="w-[242px] flex">
                  <div class="flex items-center mr-[24px]">
                      <label for="values" class="text-[#2E2E2E] text-[15px] mr-[8px]">Группировать:</label>
                      <select name="values" id="values"
                              class="background text-[#2E2E2E] pl-[4px] pr-[12px] appearance-none text-[13px] font-semibold h-[31px] w-[180px] border rounded-l outline-none">
                              <option value="date" class="outline-none">По дате</option>
                      </select>
                  </div>
                  <div class="flex items-center">
                      <p class="text-[#2E2E2E] text-[15px] mr-[8px]">Вид:</p>
                      <div class="flex">
                          <button class="w-[30px] h-[30px] flex justify-center items-center border rounded-xl bg-[#EAEAEA]">
                              <img src="../components/icons/list-icon.svg" alt="" class="">
                          </button>
                          <button class="w-[30px] h-[30px] flex justify-center items-center border rounded-xl ml-[8px]">
                              <img src="../components/icons/calendar-icon.svg" alt="" class="">
                          </button>
                      </div>
                  </div>
                </div>
              <div class="text-[13px] flex">
                <button class="h-[31px] w-[125px] rounded-xl border outline-none"
                        @click="activeSection = 1"
                        :class="{'disabled: h-[31px] w-[125px] rounded-xl border text-[#2E2E2E]cursor-not-allowed  pointer-events-none bg-[#EEEEEE] font-semibold pointer-events:none':activeSection === 1,
                                'text-[#2E2E2E] bg-white font-normal hover:duration-500 hover:bg-[#EEEEEE] hover:font-semibold':activeSection !== 1}"
                        >Все операции
                </button>
                <button class="h-[31px] mx-[8px] w-[90px] rounded-xl border text-[#2E2E2E] hover:duration-500 hover:bg-[#EEEEEE] hover:font-semibold outline-none"
                        :class="{'disabled:cursor-not-allowed  pointer-events-none bg-[#EEEEEE] font-semibold  pointer-events:none':activeSection === 2,
                                'h-[31px] w-[125px] rounded-xl border text-[#2E2E2E] bg-white font-normal':activeSection !== 2}"
                        @click="activeSection = 2">Будущие
                </button>
                <button class="h-[31px] border w-[115px] rounded-xl text-[#2E2E2E] hover:duration-500 hover:bg-[#EEEEEE] hover:font-semibold outline-none"
                        :class="{'disabled:cursor-not-allowed  pointer-events-none bg-[#EEEEEE] font-semibold  pointer-events:none':activeSection === 3,
                                'bg-white font-normal':activeSection !== 3}"
                        @click="activeSection = 3">Прошедшие
                </button>
              </div>
            </div>
            <div class="flex flex-col">
                <div class="">
                    <h1 class="text-[32px] pb-[13px] border-b">Сегодня, 10 июля</h1>
                      <draggable
                          class="list-group"
                          :list="list1"
                          group="people"
                          @change="replace"
                          itemKey="name"
                      > 
                          <template #item="{element}">
                              <div class="w-[1056px] h-[70px] flex items-center">
                                  <div class="w-[30px] h-[30px] rounded-l flex justify-center items-center ml-" :class="{'bg-[#D7EAE3]':element.profit,
                                                                         'bg-[#FFD3C2]':!element.profit}">
                                      <img v-if="element.profit" src="../components/icons/Vector%20(Stroke).svg" alt="" class="">
                                      <img v-else src="../components/icons/Vector%20(Unstroke).svg" alt="" class="">
                                  </div>
                                  <div class="ml-[16px] w-[250px]">
                                      <p class="text-[14px]">{{ element.name }}</p>
                                      <p class="text-[12px] text-[#2E2E2E]"><span class="opacity-60">Со счёта: </span>{{ element.bank}}</p>
                                  </div>
                                  <div class="ml-[10px] w-[170px]">
                                      <p class="text-[14px]">{{ element.recipient }}</p>
                                      <p class="text-[12px] text-[#2E2E2E] opacity-60">{{ element.reason }}</p>
                                  </div>
                                  <div class="ml-[30px] text-[14px] w-[240px]" v-html="element.description.replaceAll('\n', `<br>`)">
                                  </div>
                                  <div class="ml-[60px] mr-[70px] w-[82px] h-[28px] text-[12px] rounded-xl flex justify-center items-center"
                                                                   :class="{'bg-[#D7EAE3] text-[#167951]':element.status,
                                                                   'bg-[#FFD3C2] text-[#E04F1A]':element.status === false}">
                                      <p v-if="element.status" class="">Оплачен</p>
                                      <p v-else class="">Не оплачен</p>
                                  </div>
                                  <div class="w-[120px] text-[16px]">
                                    <p class="text-right" :class="{'text-[#1A8D5F]':element.profit,
                                                           'text-[#E04F1A]':!element.profit}">{{element.moneyChange}}</p>
                                  </div>
                              </div>
                          </template>
                      </draggable>
                </div>
                <div class="">
                    <h1 class="text-[32px] pb-[13px] border-b">Вчера, 9 июля</h1>
                    <draggable
                    class="list-group"
                    :list="list2"
                    group="people"
                    @change="replace"
                    itemKey="name"
                >
                      <template #item="{element}">
                        <div class="w-[1056px] h-[70px] flex items-center">
                          <div class="w-[30px] h-[30px] rounded-l flex justify-center items-center ml-" :class="{'bg-[#D7EAE3]':element.profit,
                                                                         'bg-[#FFD3C2]':!element.profit}">
                            <img v-if="element.profit" src="../components/icons/Vector%20(Stroke).svg" alt="" class="">
                            <img v-else src="../components/icons/Vector%20(Unstroke).svg" alt="" class="">
                          </div>
                          <div class="ml-[16px] w-[250px]">
                            <p class="text-[14px]">{{ element.name }}</p>
                            <p class="text-[12px] text-[#2E2E2E]"><span class="opacity-60">Со счёта: </span>{{ element.bank}}</p>
                          </div>
                          <div class="ml-[10px] w-[170px]">
                            <p class="text-[14px]">{{ element.recipient }}</p>
                            <p class="text-[12px] text-[#2E2E2E] opacity-60">{{ element.reason }}</p>
                          </div>
                          <div class="ml-[30px] text-[14px] w-[240px]" v-html="element.description.replaceAll('\n', `<br>`)">
                          </div>
                          <div class="ml-[60px] mr-[70px] w-[82px] h-[28px] text-[12px] rounded-xl flex justify-center items-center"
                               :class="{'bg-[#D7EAE3] text-[#167951]':element.status,
                                                                   'bg-[#FFD3C2] text-[#E04F1A]':element.status === false}">
                            <p v-if="element.status" class="">Оплачен</p>
                            <p v-else class="">Не оплачен</p>
                          </div>
                          <div class="w-[120px] text-[16px]">
                            <p class="text-right" :class="{'text-[#1A8D5F]':element.profit,
                                                           'text-[#E04F1A]':!element.profit}">{{element.moneyChange}}</p>
                          </div>
                        </div>
                      </template>
                    </draggable>
                </div>
              <RawDisplayer class="col-3" :value="list1" title="List 1" />

              <RawDisplayer class="col-3" :value="list2" title="List 2" />
            </div>

      </div>
    <div class="ml-[16px]  h-[748px] bg-[#F5F5F5] rounded-xl  pt-[27px]">
        <div class="px-[36px]">
          <div class="flex justify-between items-center mb-[15px]">
              <div class=""><p class="text-[22px]">Все деньги</p></div>
              <div class=""><img src="../components/images/logo.png" alt="" class=""></div>
          </div>
          <div class="w-[240px] h-[176px] bg-[#EEEEEE] mb-[26px] rounded-xl relative">
            <div class="mt-[11px] border-b-2 flex flex-col h-[97px]">
              <h1 class="pl-[28px] text-[28px] mb-[6px] h-[34px]">738 801 ₴</h1>
                  <div class="ml-[18px] flex">
                      <img src="../components/images/Vector.png" alt="" class="absolute top-[35px] left-[18px]">
                      <div class="ml-[6px] flex flex-col pl-[13px] font-semibold">
                          <p class="text-[14px] h-[17px] pb-[2px]">546 568 ₴</p>
                          <p class="text-[14px] h-[17px]">8 797 $ <span class="text-gray-500">(237 233 ₴)</span></p>
                      </div>

                  </div>
            </div>
            <div class="mx-[18px] mt-[11px] mb-[13px] h-[79px] flex justify-between">
                <div class="text-[12px] ">
                  <p class="text-gray-500">monobank</p>
                  <p class="text-gray-500">monobank, $</p>
                  <p class="text-gray-500">Касса</p>
                </div>
                <div class="text-[12px] text-right">
                  <p class="">312 471 ₴</p>
                  <p class="">8 797 $</p>
                  <p class="">234 097 ₴</p>
                </div>
            </div>
          </div>
          <div class="w-[240px] mb-[57px]">
              <ul class="h-[323px]">
                  <MenuItems v-for="item in menuItems" :key="item.index" :post="item"
                  />
              </ul>
          </div>
        </div>
          <div class="h-[86px] py-[22px] pl-[26px] pr-[42px] border bg-[#EEEEEE] relative">
              <div class="flex">
                  <div class=" pt-[3px] ">
                      <img src="../components/images/avatar.png" alt="" class="">
                  </div>
                  <div class="flex flex-col justify-center ml-[15px]">
                      <div class="text-[15px]">Сергей Василенко</div>
                      <div class="text-[15px] text-[#2E2E2E]">Newage Systems</div>
                  </div>
              </div>
              <img src="../components/icons/settings-icon.svg" alt="" class="absolute top-6 right-[32px] outline-none">
              <img src="../components/icons/help.svg" alt="" class="absolute bottom-4 right-[32px] outline-none">
          </div>

    </div>
    <div class="absolute text-[32px] pb-[7px] bottom-[32px] w-[66px] h-[66px] bg-[#2E2E2E] rounded-[50%] flex justify-center items-center text-white cursor-pointer outline-none">
      +
    </div>
  </div>
</template>

<style>
.filter:before{
  content: "";
  display: block;
  background: url("../components/icons/filter-icon.svg") no-repeat;
  width: 16px;
  height: 16px;
  margin: 2px 7px 0 0
}
.filter:after{
  content: "";
  display: block;
  background: url("./src/components/icons/arrow-down.svg") no-repeat;
  width: 12px;
  height: 8px;
  margin: 8px 0 0 8px;
}
.image:before{
  content: "";
  display: block;
  position: absolute;
  background: url("./src/components/images/favorite.png") no-repeat;
  width: 12px;
  height: 12px;
  margin: 0 0 0 0;
}
.background{
  background: url('../src/components/icons/arrow-down.svg') no-repeat right;
  background-position-x: calc(100% - 13px);
}
</style>