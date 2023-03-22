<script lang="ts">
  import BreweryCard from "./components/BreweryCard.svelte";
  import { Col, Container, Row, Modal } from "sveltestrap";
  import { getBreweries } from "./api/HttpClient";

  let breweries: any[] = [];

  let open = false;
  const toggle = () => open = !open;
  let highlighted;
  const setHighlightedBeerType = (selectedBrewery) => {
    highlighted = selectedBrewery;
    toggle();
  }

  getBreweries().then((data) => {
      // Kanskje litt spaghetti, hehe.
      let ModifisertLufttrykk = data.map(({Lufttrykk, Timestamp, ...rest}) => ({Lufttrykk: Math.floor(Math.random() * 1501), Timestamp: Timestamp.split("T")[0], ...rest}));
      breweries = ModifisertLufttrykk
    })
  
</script>

<main>
  <Modal body header="Info for selected beer" isOpen={open} {toggle}>
    <h2>BeerName: {highlighted.brewery_name}</h2>
    <p>
      <strong>Fuktighet:</strong> {highlighted.Humidity} 🌊
    </p>
    <p>
      <strong>Trykk:</strong> {highlighted.Pressure} 💨
    </p>
  </Modal>
  <Container>
    <Row>
      <Col>
        <h1>Svelte + twoday</h1>
      </Col>
    </Row>
    <Row>
      <Col>
        <p>
          Check out <a
            href="https://svelte.dev/tutorial"
            target="_blank"
            rel="noreferrer">the docs</a
          >
        </p>
      </Col>
    </Row>
    <Row cols={3}>
      {#each breweries as brewery}
        <Col>
          <BreweryCard onClick={() => setHighlightedBeerType(brewery)} {brewery} />
        </Col>
      {:else}
        <Col>
          <p>loading...</p>
        </Col>
      {/each}
    </Row>
  </Container>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
