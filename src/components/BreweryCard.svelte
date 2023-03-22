<script lang="ts">
  import {
    Card,
    CardBody,
    CardFooter,
    CardHeader,
    CardText,
    CardTitle,
  } from "sveltestrap";

  export let brewery: any;
  export let onClick: (e: any) => void;
</script>
<!-- 
  , denne blir lang og stygg. Men jeg liker å leve farlig. 
  Den sprenger egentlig på 1500, men jeg puttern på 1300 sånn at vi faktisk kan se det størsteparten av tiden
-->
<Card on:click={onClick}
  color="{brewery.Lufttrykk >= 999.00 && brewery.Lufttrykk < 1199 ? "warning" : brewery.Lufttrykk >= 1200 ? "danger" : "primary"}" 
  class="mb-3">
  <CardHeader>
    <CardTitle>{brewery.beer_name}</CardTitle>
  </CardHeader>
  <CardBody>
    <!-- <CardSubtitle>{brewery.Enhet}</CardSubtitle> -->
    <CardText>
      <p>
        <strong>Temp:</strong> {brewery.Temperature} 🌡️
      </p>
    </CardText>
  </CardBody>
  <CardFooter>{brewery.Timestamp}</CardFooter>
</Card>
