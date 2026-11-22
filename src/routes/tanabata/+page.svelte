<script>
  import CardContent from "$lib/components/card/card-content.svelte";
  import Card from "$lib/components/card/card.svelte";
  import Container from "$lib/components/Container.svelte";
  import Button from "$lib/components/Button.svelte";
  
  import { fade } from "svelte/transition";
  import CardHeader from "$lib/components/card/card-header.svelte";
  import CardTitle from "$lib/components/card/card-title.svelte";
  import CardFooter from "$lib/components/card/card-footer.svelte";

  import { Sakura } from "$lib/components/sakura";
  import "$lib/components/sakura.css";
  import { onMount } from "svelte";

//   let flipped = $state();

  const wishArr = [
    "ชัยชนะที่ยิ่งใหญ่เป็นวินัยที่เราถักทอในทุกๆวัน",
    "อดทนอ่านหนังสือให้สอบติดภายในปีนี้ ดีกว่าต้องอ่านหนังสือสอบไปอีกปีหน้า",
    "ถ้าเราไม่ลงมือทำตอนนี้ อะไรก็เป็นไปไม่ได้!!",
    "เมื่อไหร่ที่ขี้เกียจอ่านหนังสือ เมื่อนั้นโอกาสเป็นของคนอื่น",
    "จะสอบแล้วหนังสือก็อ่าน แถมเน้นอธิษฐานอีกด้วย",
    "อนาคตขึ้นอยู่กับสิ่งที่เราลงมือทำวันนี้ไม่ใช่วันพรุ่งนี้",
    "เวลาเตรียมตัวสอบของเรามีค่าทุกวินาทีอยู่ที่ว่าเราจะใช้มันคุ้มค่ามากแค่ไหน",
    "หนึ่งวันที่ขี้เกียจอ่านหนังสืออาจเป็นหนึ่งคะแนนที่หายไปเลย",
    "จุดมุ่งหมายอยู่ไม่ไกลขอเพียงอย่าถอดใจในการอ่านหนังสือ",
    "คู่แข่งที่น่ากลัวที่สุดคือความขี้เกียจของเราเอง",
    "โอกาสดีๆไม่ได้มีบ่อยเมื่อได้โอกาสสอบจงทำให้เต็มที่!",
    "ทุกๆความสำเร็จย่อมเกิดจากความพยายามเสมอ",
    "แค่ล้มครั้งนี้ ไม่ได้แปลว่ายอมแพ้",
    "เป้าหมายอยู่ไม่ไกลขอเพียงไม่ถอดใจกับคำดูถูกระหว่างทาง",
    "ไม่มีความสำเร็จไหนไม่ต้องใช้ความพยายามการสอบก็เช่นกัน",
    "บรรยากาศสนามสอบอาจกดดันแต่ถ้ามีฝันต้องฟันฝ่าให้ได้",
    "อ่านหนังสือหลายวันเพื่อสอบวันนี้อย่ายอมแพ้!",
    "เธอเก่งที่สุด!",
    "คาดหวังได้แต่หากผิดหวังก็แค่ยอมรับและเดินต่อไป",
    "แค่ยิ้มุกอย่างจะง่ายขึ้น!!",
    "เมื่อไหร่ที่ขี้เกียจอ่านหนังสือเมื่อนั้นโอกาสเป็นของคนอื่น",
    "อย่าลดขนาดของความฝันแต่ให้เพิ่มความขยันและการลงมือทำ",
    "มีคนมากมายเอาความสำเร็จไปฝากครอบครัวเราก็ต้องเป็นหนึ่งในนั้น!",
    "วินาทีที่เข้มแข็งที่สุดไม่ใช่วินาทีแห่งชัยชนะแต่เป็นวินาทีที่เราไม่ยอมแพ้",
    "แม้เส้นทางฝันอาจทำให้ท้อแท้จงเปลี่ยนความท้อแท้เป็นท้าทาย",
  ];

  let wish1, wish2, wish3, wish4;

  function randomWish(id) {
    var r = Math.floor(Math.random() * wishArr.length) + 1;

    if (id === 1) {
      wish1 = wishArr[r];
    } else if (id === 2) {
      wish2 = wishArr[r];
    } else if (id === 3) {
      wish3 = wishArr[r];
    } else if (id === 4) {
      wish4 = wishArr[r];
    }
  }

  let visible1 = $state(false);
  let visible2 = $state(false);
  let visible3 = $state(false);
  let visible4 = $state(false);

  onMount(() => {
    var sakura = new Sakura("body", {
      colors: [
        {
          gradientColorStart: "rgba(255, 183, 197, 0.9)",
          gradientColorEnd: "rgba(255, 197, 208, 0.9)",
          gradientColorDegree: 120,
        },
        {
          gradientColorStart: "rgba(255,189,189)",
          gradientColorEnd: "rgba(227,170,181)",
          gradientColorDegree: 120,
        },
        {
          gradientColorStart: "rgba(212,152,163)",
          gradientColorEnd: "rgba(242,185,196)",
          gradientColorDegree: 120,
        },
      ],
      delay: 2000,
    });
  });
</script>

<div class="flex flex-1 flex-col items-center justify-center bg-[url('/bg2.png')] bg-no-repeat bg-cover relative before:absolute before:inset-0 before:bg-background/60 overflow-hidden"
>
  <Container>
    <Card class="w-fit mx-auto">
      <CardHeader>
        <CardTitle class="text-lg font-semibold">อ่านคําอวยพรจากดวงดาว</CardTitle>
      </CardHeader>
      <CardContent>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 *:mx-auto">
          <div class="relative w-50 h-70 sm:w-55 sm:h-75 md:w-60 md:h-80"
               style="perspective: 1000px; box-shadow: rgba(0, 0, 0, 0.2) 0px 4px 15px; border-radius: 16px; translate: none; rotate: none;
               scale: none; opacity: 1; transform: translate(0px, 0px);"
          >
            <div class="absolute inset-0 pointer-events-none z-50 overflow-visible"></div>
            <div class="relative w-full h-full" style="transform-style: preserve-3d; translate: none; rotate: none; scale: none; transform: translate(0px, 0px);">
              <div class="absolute inset-0 rounded-2xl bg-linear-to-br from-red-400 to-rose-600 flex flex-col items-center justify-center p-4" style="backface-visibility:hidden">
                <div class="absolute inset-0 flex flex-col items-center justify-center text-[200px] opacity-20">
                  6
                </div>
                <div class="absolute top-0 left-1/2 -translate-x-1/2 w-8 h-12 flex flex-col items-center">
                  <div class="w-1 h-8 bg-red-700 rounded-full"></div>
                  <div class="w-6 h-6 rounded-full border-4 border-red-700"></div>
                </div>
                <div class="text-2xl sm:text-3xl font-bold text-white drop-shadow-lg">
                  <Button
                    onclick={() => {
                      visible1 = !visible1;
                      randomWish(1);
                    }}
                    class="text-2xl bg-linear-to-br from-amber-600 to-yellow-600 cursor-pointer">คำอวยพรวันนี้</Button>
                </div>
                <div class="sakurafont_421e93e7-module__ZDjIua__className text-white text-lg sm:text-xl mt-4 tracking-wide">
                  {#if visible1}
                    <p transition:fade={{ duration: 1000 }}>
                      {wish1}
                    </p>
                  {/if}
                </div>
                <div class="absolute bottom-4 flex gap-2">
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                </div>
              </div>
            </div>
          </div>
          <!-- card2 -->
          <div
            class="relative w-50 h-70 sm:w-55 sm:h-75 md:w-60 md:h-80"
            style="perspective: 1000px; box-shadow: rgba(0, 0, 0, 0.2) 0px 4px 15px; border-radius: 16px; translate: none; rotate: none;
                   scale: none; opacity: 1; transform: translate(0px, 0px);"
          >
            <div class="absolute inset-0 pointer-events-none z-50 overflow-visible"></div>
            <div class="relative w-full h-full" style="transform-style: preserve-3d; translate: none; rotate: none; scale: none; transform: translate(0px, 0px);">
              <div
                class="absolute inset-0 rounded-2xl bg-linear-to-br from-green-400 to-teal-600 flex flex-col items-center justify-center p-4"
                style="backface-visibility:hidden"
              >
              <div class="absolute inset-0 flex flex-col items-center justify-center text-[200px] opacity-20">
                  7
                </div>
                <div class="absolute top-0 left-1/2 -translate-x-1/2 w-8 h-12 flex flex-col items-center">
                  <div class="w-1 h-8 bg-red-700 rounded-full"></div>
                  <div class="w-6 h-6 rounded-full border-4 border-red-700"></div>
                </div>
                <div class="text-2xl sm:text-3xl font-bold text-white drop-shadow-lg">
                  <Button
                    onclick={() => {
                      visible2 = !visible2;
                      randomWish(2);
                    }}
                    class="text-2xl bg-linear-to-br from-blue-400 to-blue-600 cursor-pointer">คำอวยพรวันนี้</Button>
                </div>
                <div class="sakurafont_421e93e7-module__ZDjIua__className text-white text-lg sm:text-xl mt-4 tracking-wide">
                  {#if visible2}
                    <p transition:fade={{ duration: 1000 }}>
                      {wish2}
                    </p>
                  {/if}
                </div>
                <div class="absolute bottom-4 flex gap-2">
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                </div>
              </div>
            </div>
          </div>
          <!-- card4 -->
          <div
            class="relative w-50 h-70 sm:w-55 sm:h-75 md:w-60 md:h-80"
            style="perspective: 1000px; box-shadow: rgba(0, 0, 0, 0.2) 0px 4px 15px; border-radius: 16px; translate: none; rotate: none; 
                  scale: none; opacity: 1; transform: translate(0px, 0px);">
            <div class="absolute inset-0 pointer-events-none z-50 overflow-visible"></div>
            <div class="relative w-full h-full" style="transform-style: preserve-3d; translate: none; rotate: none; scale: none; transform: translate(0px, 0px);">
              <div class="absolute inset-0 rounded-2xl bg-linear-to-br from-blue-400 to-cyan-600 flex flex-col items-center justify-center p-4"style="backface-visibility:hidden">
              <div class="absolute inset-0 flex flex-col items-center justify-center text-[200px] opacity-20">
                  6
                </div>
                <div class="absolute top-0 left-1/2 -translate-x-1/2 w-8 h-12 flex flex-col items-center">
                  <div class="w-1 h-8 bg-red-700 rounded-full"></div>
                  <div class="w-6 h-6 rounded-full border-4 border-red-700"></div>
                </div>
                <div class="text-2xl sm:text-3xl font-bold text-white drop-shadow-lg">
                  <Button
                    onclick={() => {
                      visible3 = !visible3;
                      randomWish(3);
                    }}
                    class="text-2xl bg-linear-to-br from-green-400 to-teal-600 cursor-pointer">คำอวยพรวันนี้</Button>
                </div>
                <div class="sakurafont_421e93e7-module__ZDjIua__className text-white text-lg sm:text-xl mt-4 tracking-wide">
                  {#if visible3}
                    <p transition:fade={{ duration: 1000 }}>
                      {wish3}
                    </p>
                  {/if}
                </div>
                <div class="absolute bottom-4 flex gap-2">
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                </div>
              </div>
            </div>
          </div>
          <!-- card5 -->
          <div
            class="relative w-50 h-70 sm:w-55 sm:h-75 md:w-60 md:h-80"
            style="perspective: 1000px; box-shadow: rgba(0, 0, 0, 0.2) 0px 4px 15px; border-radius: 16px; translate: none; rotate: none; 
                  scale: none; opacity: 1; transform: translate(0px, 0px);"
          >
            <div class="absolute inset-0 pointer-events-none z-50 overflow-visible"></div>
            <div
              class="relative w-full h-full"
              style="transform-style: preserve-3d; translate: none; rotate: none; scale: none; transform: translate(0px, 0px);"
            >
              <div
                class="absolute inset-0 rounded-2xl bg-linear-to-br from-amber-400 to-yellow-600 flex flex-col items-center justify-center p-4"
                style="backface-visibility:hidden"
              >
              <div
                  class="absolute inset-0 flex flex-col items-center justify-center text-[200px] opacity-20"
                >
                  7
                </div>
                <div
                  class="absolute top-0 left-1/2 -translate-x-1/2 w-8 h-12 flex flex-col items-center"
                >
                  <div class="w-1 h-8 rounded-full bg-red-700"></div>
                  <div
                    class="w-6 h-6 rounded-full border-4 border-red-700"
                  ></div>
                </div>
                <div
                  class="text-2xl sm:text-3xl font-bold text-white drop-shadow-lg"
                >
                  <Button
                    onclick={() => {
                      visible4 = !visible4;
                      randomWish(4);
                    }}
                    class="text-2xl bg-linear-to-br from-red-400 to-rose-600 cursor-pointer"
                    >คำอวยพรวันนี้</Button
                  >
                </div>
                <div class=" text-white text-lg sm:text-xl mt-4 tracking-wide">
                  {#if visible4}
                    <p transition:fade={{ duration: 1000 }}>
                      {wish4}
                    </p>
                  {/if}
                </div>
                <div class="absolute bottom-4 flex gap-2">
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                  <div class="w-2 h-2 rounded-full bg-white/60"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </CardContent>
      <CardFooter>
        <p class="font-semibold text-2xl text-center w-full">
          🎍 ขอให้โชคดีและสมหวังในทุกความปรารถนา 🎊
        </p>
      </CardFooter>
    </Card>
  </Container>
  <!-- <div class="mt-5 font-bold text-4xl">
        <p>คำอวยพร</p>
    </div> -->
</div>
