<script lang="ts">
    import { onMount } from "svelte";
  import {
    Card,
    CardBody,
    CardFooter,
    CardHeader,
    CardSubtitle,
    CardText,
    CardTitle,
  } from "sveltestrap";

  export let brewery: any;

  onMount( () => {
    
  })

</script>
<!-- 
  , denne blir lang og stygg. Men jeg liker å leve farlig. 
  Den sprenger egentlig på 1500, men jeg puttern på 1300 sånn at vi faktisk kan se det størsteparten av tiden
-->
<Card color="{brewery.Lufttrykk >= 999.00 && brewery.Lufttrykk < 1199 ? "warning" : brewery.Lufttrykk >= 1200 ? "danger" : "primary"}" class="mb-3">
  <CardHeader>
    <CardTitle>{brewery.Rom}</CardTitle>
  </CardHeader>
  <CardBody>
    <CardSubtitle>{brewery.Enhet}</CardSubtitle>
    <CardText>
      <p>
        <strong>Temp:</strong> {brewery.Temperatur} 🌡️
      </p>
      <p>
        <strong>Fuktighet:</strong> {brewery.Fuktighet} 🌊
      </p>
      <p>
        <strong>Trykk:</strong> {brewery.Lufttrykk} 💨
      </p>
    </CardText>
  </CardBody>
  <CardFooter>{brewery.Timestamp}</CardFooter>
</Card>
