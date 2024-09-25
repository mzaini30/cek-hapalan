<script>
  import { acak } from "kumpulan-tools";
  import Swal from "sweetalert2";
  let terpilih = [];
  let semuaDataFinal = [];
  let yangDites = 0;
  function tes() {
    let semuaData = [];
    for (let x of terpilih) {
      let halamanIni = [];
      for (let y = 2; y <= 21; y++) {
        halamanIni = [...halamanIni, y + (x - 1) * 20];
      }
      semuaData = [...semuaData, ...halamanIni];
      semuaDataFinal = semuaData;
    }
    yangDites = acak(semuaData)[0];
    Swal.fire(`Tes halaman ${yangDites}`);
  }
</script>

<div class="pt-3 px-3 pb-20">
  <!-- {JSON.stringify(semuaDataFinal)} -->
  <!-- {terpilih}{yangDites} -->
  <!-- {semuaDataFinal} -->
  <div class="grid grid-cols-3 gap-3">
    {#each Array(30) as x, n}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <div
        class="bg-gray-200 rounded-50% aspect-square items-center justify-center flex text-3xl cursor-pointer select-none {terpilih.includes(
          n + 1,
        ) && 'bg-green-300'}"
        on:click={() => {
          if (terpilih.includes(n + 1)) {
            terpilih = terpilih.filter((x) => x !== n + 1);
          } else {
            terpilih = [...terpilih, n + 1];
          }
        }}
      >
        {n + 1}
      </div>
    {/each}
  </div>
  {#if terpilih.length > 0}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="w-full p-3 fixed bottom-0 left-0" on:click={tes}>
      <div
        class="bg-green-500 text-white p-2 font-bold text-center select-none cursor-pointer rounded"
      >
        TES
      </div>
    </div>{/if}
</div>
