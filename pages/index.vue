<template>
  <section class="container">
    <div class="grid auto-fill">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>4</div>
      <div>5</div>
      <div>6</div>
    </div>
    <div class="grid auto-fit">
      <div>1</div>
      <div>2</div>
    </div>
    <div class="grid auto-fill-limited">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>4</div>
      <div>5</div>
      <div>6</div>
      <div>7</div>
      <div>8</div>
      <div>9</div>
    </div>

  <div class="page">
    <header id="pageHeader">Header</header>
    <article id="mainArticle">Article</article>
    <nav id="mainNav">Nav</nav>
    <div id="siteAds">Ads</div>
    <footer id="pageFooter">Footer</footer>    
  </div>
  </section>
</template>

<script>
export default {
}
</script>

<style lang="scss">
$squareSize: 200px;

@function pixel2Ratio($pixel){
  @return 100vw * $pixel / 1440px;
}

.grid { 
  display: grid;
  grid-gap: 2vw;
  border: 1px solid black;
  margin: 10px;
  }
.grid > div {
  font-size: 5vw;
  padding: 15px;
  display:inline-block;
  background: gold;
  text-align: center;
  height: pixel2Ratio($squareSize);
}
.auto-fill {
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
}
.auto-fit {
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
}
.auto-fill-limited {
  grid-template-columns: repeat(auto-fill, minmax(pixel2Ratio($squareSize), 1fr));
  margin: 100px;
}

// NOTE: Set grid area
.page {
  display: grid;
  grid-template-areas: 
    "header header header"
    "nav article ads"
    "footer footer footer";
  
  // NOTE: Vertical
  grid-template-rows: 80px 1fr 70px;

  // NOTE: Horizontal
  grid-template-columns: 20% 1fr 15%;
  grid-row-gap: 10px;
  grid-column-gap: 10px;
  height: 100vh;
  margin: 0;

  header, footer, article, nav, div {
    padding: 1.2em;
    background: gold;
    }
  #pageHeader {
    grid-area: header;
    }
  #pageFooter {
    grid-area: footer;
    }
  #mainArticle { 
    grid-area: article;      
    }
  #mainNav { 
    grid-area: nav; 
    }
  #siteAds { 
    grid-area: ads; 
    } 
}

/* Stack the layout on small devices/viewports. */
@media all and (max-width: 575px) {
  .page { 
    // display:block;
    grid-template-areas: 
      "header"
      "article"
      "ads"
      "nav"
      "footer";
    grid-template-rows: 80px 1fr 70px 1fr 70px;  
    grid-template-columns: 1fr;
  }
}
</style>
