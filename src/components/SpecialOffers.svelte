<script>
  export let offers = [];
  export let onBook = () => {};

  function money(v) {
    return "£" + Number(v).toLocaleString("en-GB");
  }
</script>

<section id="offers" class="offers">
  <div class="offers-head">
    <h2 class="section-title">Special offers</h2>
    <p class="offers-lead">
      Four homes at 7% off the list price until 31 December.
    </p>
  </div>

  <div class="offers-list">
    {#each offers as offer}
      <article class="offer">
        <img
          class="offer-photo"
          src={offer.photo}
          alt={offer.alt}
          loading="lazy"
        />
        <p class="offer-place">{offer.building}, floor {offer.floor}</p>
        <h3 class="offer-title">{offer.title}</h3>
        <p class="offer-note">{offer.note}</p>
        <p class="offer-price">
          {money(offer.price)}
          <span class="offer-old">{money(offer.oldPrice)}</span>
        </p>
        <button
          class="offer-book"
          type="button"
          aria-label={"Book a viewing, home " + offer.id}
          on:click={onBook}
        >
          Book a viewing
        </button>
      </article>
    {/each}
  </div>
</section>

<style>
  .offers {
    padding: 160px var(--margin);
    background: var(--bg);
  }

  .offers-head {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 76px;
  }

  .offers-head .section-title {
    font-size: 64px !important;
  }

  .offers-lead {
    max-width: 360px;
    margin: 8px 60px 0 0 !important;
    font-size: 24px;
    line-height: 1.35;
  }

  .offers-list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: var(--gutter);
  }

  .offer-photo {
    display: block;
    width: 100%;
    aspect-ratio: 4 / 5;
    object-fit: cover;
  }

  .offer-place {
    margin-top: 20px !important;
    font-size: 14px;
    line-height: 1.4;
    color: var(--muted);
  }

  .offer-title {
    margin-top: 6px !important;
    font-size: 24px;
    line-height: 1.3 !important;
  }

  .offer-note {
    margin-top: 8px !important;
    font-size: 14px;
    line-height: 1.4;
    color: var(--muted);
  }

  .offer-price {
    margin-top: 20px !important;
    font-size: 24px;
    font-weight: 500;
    line-height: 1.3;
    font-variant-numeric: tabular-nums;
  }

  .offer-old {
    margin-left: 12px;
    font-size: 14px;
    font-weight: 400;
    color: var(--muted);
    text-decoration: line-through;
  }

  .offer-book {
    margin-top: 20px;
    padding: 0;
    border: 0;
    background: none;
    font-size: 18px;
    line-height: 1.4;
    cursor: pointer;
    text-decoration: underline;
    text-decoration-thickness: 1px;
    text-underline-offset: 0.2em;
  }

  /* Планшет */
  @media (max-width: 1023px) {
    .offers {
      padding: 120px 32px;
    }

    .offers-head {
      display: block;
      margin-bottom: 40px;
    }

    .offers-head .section-title {
      font-size: 48px !important;
    }

    .offers-lead {
      max-width: 320px;
      margin: 16px 0 0 !important;
      font-size: 20px;
      line-height: 1.4;
    }

    .offers-list {
      grid-template-columns: repeat(2, 1fr);
      gap: 48px 24px;
    }
  }

  /* Телефон */
  @media (max-width: 599px) {
    .offers {
      padding: 96px 16px;
    }

    .offers-head {
      margin-bottom: 32px;
    }

    .offers-lead {
      max-width: none;
    }

    .offers-head .section-title {
      font-size: 34px !important;
    }

    .offers-list {
      display: flex;
      gap: 12px;
      margin: 0 -16px;
      padding: 0 16px;
      overflow-x: auto;
      scroll-snap-type: x mandatory;
      scroll-padding-left: 16px;
      scrollbar-width: none;
    }

    .offer {
      flex: none;
      width: 280px;
      scroll-snap-align: start;
    }

    .offer-photo {
      aspect-ratio: 280 / 408;
    }

    .offer-title {
      font-size: 20px;
    }
  }
</style>
