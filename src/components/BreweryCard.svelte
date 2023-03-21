<script lang="ts">
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
</script>

<Card class="mb-3">
  <CardHeader>
    <CardTitle>{brewery.Rom}</CardTitle>
  </CardHeader>
  <CardBody>
    <CardSubtitle>{brewery.Enhet}</CardSubtitle>
    <CardText>
      <p>
        Temp: {brewery.Temperatur}
      </p>
      <p>
        Fuktighet: {brewery.Fuktighet}
      </p>
      <p>
        Trykk: {brewery.Lufttrykk}
      </p>
    </CardText>
  </CardBody>
  <CardFooter>{brewery.Timestamp}</CardFooter>
</Card>
