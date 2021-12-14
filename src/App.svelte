<script>
  import mnjs from 'mnjs';

  import Line from 'svelte-chartjs/src/Line.svelte';
  import Bar from 'svelte-chartjs/src/Bar.svelte';
  import Radar from 'svelte-chartjs/src/Radar.svelte';

  // 2D Rotation Matrix
  const ROTATION_MATRIX_2D = mnjs.range(0, 360, 15);

  // Color Manipulation
  const randomRedColor = mnjs.rib(0, 204),
    randomGreenColor = mnjs.rib(0, 100),
    randomBlueColor = mnjs.rib(0, 240),
    randomOpacity = mnjs.divi(mnjs.rib(1, 8), 10);

  // Adjust Point Radius
  const pointRadius = mnjs.rib(4, 11);

  // Chart Data
  const data = {
    labels: ROTATION_MATRIX_2D,
    datasets: [
      {
        label: '# The sin of 2D Rotation Matrix',
        data: mnjs.sin.deg(ROTATION_MATRIX_2D),
        backgroundColor: [
          `rgba(${randomRedColor}, ${randomGreenColor}, ${randomBlueColor}, ${randomOpacity})`,
        ],
        borderColor: ['rgba(27, 89, 161, 1)'],
        borderWidth: 2,
        pointRadius: `${pointRadius}`,
      },
    ],
  };
</script>

<h1>Svelte demo project using mnjs together with chartjs</h1>

<br />

<div class="chart">
  <h3>Radar Chart Example</h3>
  <div>
    <Radar
      {data}
      width={400}
      height={200}
      options={{
        maintainAspectRatio: false,
      }}
    />
  </div>
</div>

<br />

<div class="chart">
  <h3>Line Chart Example</h3>

  <div>
    <Line
      {data}
      width={400}
      height={200}
      options={{
        maintainAspectRatio: false,
      }}
    />
  </div>
</div>

<br />

<div class="chart">
  <h3>Bar Chart Example</h3>
  <div>
    <Bar
      {data}
      width={400}
      height={200}
      options={{
        maintainAspectRatio: false,
      }}
    />
  </div>
</div>

<br />

<div class="chart">
  <h3>Random Values</h3>
  <div
    style="background-color: rgb({randomRedColor}, {randomGreenColor}, {randomBlueColor}, {randomOpacity}); padding: 10px; text-align: center"
  >
    <p>
      <b
        >Color : rgb({randomRedColor}, {randomGreenColor}, {randomBlueColor}, {randomOpacity})</b
      >
    </p>
    <p>
      <b>Point Radius : {pointRadius} px</b>
    </p>
  </div>
</div>

<div style="margin: 100px 50px;">
  <h3>Links:</h3>
  <ul>
    <li>
      <b>MNJS</b>:<br />
      <a href="https://www.npmjs.com/package/mnjs" target="_blank">
        https://www.npmjs.com/package/mnjs
      </a>
      <br />
      <a href="https://github.com/dr-montasir/mnjs" target="_blank">
        https://github.com/dr-montasir/mnjs
      </a>
    </li>

    <br />

    <li>
      <b>Chart.js</b>:<br />
      <a href="https://www.chartjs.org/" target="_blank">
        https://www.chartjs.org/
      </a>
      <br />
      <a href="https://www.npmjs.com/package/svelte-chartjs" target="_blank">
        https://www.npmjs.com/package/svelte-chartjs
      </a>
    </li>
  </ul>
</div>

<div style="text-align: center;">
  <div>________________________________________________________</div>
  <br />
  <div>
    {#if new Date().getFullYear() === 2021}
      {new Date().getFullYear()}
    {:else}
      {2021} - {new Date().getFullYear()}
    {/if} All rights reserved @ https://github.com/dr-montasir
  </div>
  <div>________________________________________________________</div>
  <br />
</div>

<style>
  h1 {
    text-align: center;
  }
  .chart {
    max-width: 800px;
    min-width: 400px;
    margin: 0 auto;
  }
</style>
