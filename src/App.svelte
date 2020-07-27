<script>

let totalTroops = 0
let marches = 5
let shelter = 0
let baseMarch = 0
let armySizeBuff = 0
let reinforceMarch = baseMarch
let garrisonMarch = baseMarch + 55000
let baseMarchDisplay = baseMarch

function handleClick() {
	baseMarchDisplay = (parseInt(baseMarch * (armySizeBuff)) ) + parseInt(baseMarch)
	console.log(baseMarchDisplay)
	garrisonMarch = parseInt(baseMarchDisplay) + 55000
	reinforceMarch = parseInt(baseMarchDisplay)
}
function numberWithCommas(x) {
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}

</script>

<style>
  main {
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 2.5em;
    font-weight: 100;
    margin: 0 auto 2rem auto;
    width: 100%;
    text-align: center;
	}
	label {
		min-width: 8rem;
		display: inline-block;
	}

  @media (min-width: 640px) {
    main {
      max-width: 960px;
    }
	}
	.small {
		font-size: 0.75rem;
		color: #777;
	}
</style>

<main>
  <h1>Can You Blank?</h1>
    <div>
      <label for="totaltroops">Total Troops</label>
      <input type="number" name="totaltroops" id="totaltroops" bind:value={totalTroops} autofocus />
    </div>
    <div>
      <label for="shelter">Shelter Capacity</label>
      <input type="number" name="shelter" id="shelter" bind:value={shelter} />
    </div>
    <div>
      <label for="basemarch">Base March Size</label>
      <input type="basemarch" name="basemarch" id="basemarch" bind:value={baseMarch} />
    </div>
    <div>
      <label for="armybuff">Army Size Buff</label>
      <select name="armybuff" id="armybuff" bind:value={armySizeBuff}>
        <option value="0">0</option>
        <option value="0.2">20%</option>
        <option value="0.5">50%</option>
        <option value="0.75">75%</option>
      </select>
    </div>
    <div>
      <label for="marches">Total Marches</label>
      <select name="marches" id="marches" bind:value={marches}>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5" selected="selected">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
      </select>
    </div>
		<div>
			<button on:click={handleClick}>Calculate</button>
		</div>
		<hr>
		<div>
		<p>Reinforcment March Size - {numberWithCommas(reinforceMarch)}</p>
		<p>Garrison/Battle March Size - {numberWithCommas(garrisonMarch)} <span class="small">(Assumes all Rank VIII commanders)</span></p>
		<p>Blankable Troops all Garrison - {numberWithCommas(parseInt(marches - 1) * garrisonMarch + shelter)}</p>
		<p>Blankable Troops all Reinforce - {numberWithCommas(parseInt(marches - 1) * reinforceMarch + shelter)}</p>
		</div>
</main>
