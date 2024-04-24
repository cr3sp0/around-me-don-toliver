<script lang="ts">
    import { onMount } from "svelte";
    import { onDestroy } from 'svelte';
    import { fade } from "svelte/transition";
    export const prerender = true;

    let mobile = 25;
    let buttonVisible = true;
    let playlist = false;
    let caricato = false;
    let title = 0;
    let subtitle = 0;
    
    
    onMount(() => {
        caricato = true;
        if (window.innerWidth>= 600) {
      title = 5;
      subtitle = 1.5;
    } else {
      title = 10;
      subtitle = 3;
    }
    })

    function page() {
        buttonVisible = false;
        mobile = 5;
        title = title-3;
        subtitle = subtitle-.75;
        playlist = true;
      //window.location.href = "/main";
    }

    function removeButton() {
    buttonVisible = false;
  }
    onDestroy(() => {
      removeButton();
    });
</script>

{#if caricato}
<div class="hero" id="hero" in:fade={{ delay:250 , duration: 2000}} style="margin-top: {mobile}vh;">
    <h1 style="font-size: {title}vw;">playlist library</h1>
    <p style="font-size: {subtitle}vw;">una libreria con tutte le tue playlist</p>
</div>
<div class="femore" in:fade={{ delay:1750 , duration: 2000}}>
  {#if buttonVisible}
    <button  on:click={page} class="button-17">ACCEDI</button>
    {/if}
</div>
  {#if playlist}
  <div class="container">
    <input type="radio" name="slider" id="item-1" checked>
    <input type="radio" name="slider" id="item-2">
    <input type="radio" name="slider" id="item-3">
  <div class="cards">
    <label class="card" for="item-1" id="song-1">
      <img src="https://images.unsplash.com/photo-1530651788726-1dbf58eeef1f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=882&q=80" alt="song">
    </label>
    <label class="card" for="item-2" id="song-2">
      <img src="https://images.unsplash.com/photo-1559386484-97dfc0e15539?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80" alt="song">
    </label>
    <label class="card" for="item-3" id="song-3">
      <img src="https://images.unsplash.com/photo-1533461502717-83546f485d24?ixlib=rb-1.2.1&auto=format&fit=crop&w=900&q=60" alt="song">
    </label>
  </div>
  <div class="player">
    <div class="upper-part">
      <div class="play-icon">
        <svg width="20" height="20" fill="#2992dc" stroke="#2992dc" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="feather feather-play" viewBox="0 0 24 24">
          <defs/>
          <path d="M5 3l14 9-14 9V3z"/>
        </svg>
      </div>
      <div class="info-area" id="test">
        <label class="song-info" id="song-info-1">
          <div class="title">Bunker</div>
          <div class="sub-line">
            <div class="subtitle">Balthazar</div>
            <div class="time">4.05</div>
          </div>
        </label>
        <label class="song-info" id="song-info-2">
          <div class="title">Words Remain</div>
          <div class="sub-line">
            <div class="subtitle">Moderator</div>
            <div class="time">4.05</div>
          </div>
        </label>
        <label class="song-info" id="song-info-3">
          <div class="title">Falling Out</div>
          <div class="sub-line">
            <div class="subtitle">Otzeki</div>
            <div class="time">4.05</div>
          </div>
        </label>
      </div>
    </div>
    <div class="progress-bar">
      <span class="progress"></span>
    </div>
  </div>
</div>
  {/if}
{/if}

<style lang="scss">
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Syne:wght@400..800&display=swap');


    :global(html, body) {
      font-family: "Inter";
        background-color: #121212;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
        padding: 0;
        height: 100%;
    }
    h1 {
        transition: font-size 0.5s;
        color: #FFFFFF;
        text-transform: uppercase;
        text-align: center;
    }
    p {
        
        color: #A7A7A7;
        text-transform: uppercase;
        text-align: center;
    }

    .hero{
      width: 60vw;
      transition: margin-top 0.5s;
    }

    .femore {
        padding-top: 50px;
    }

    .button-17 {
      align-items: center;
      appearance: none;
      background-color: #fff;
      border-radius: 24px;
      border-style: none;
      box-shadow: rgba(0, 0, 0, .2) 0 3px 5px -1px,rgba(0, 0, 0, .14) 0 6px 10px 0,rgba(0, 0, 0, .12) 0 1px 18px 0;
      box-sizing: border-box;
      color: #3c4043;
      cursor: pointer;
      display: inline-flex;
      fill: currentcolor;
      font-size: 14px;
      font-weight: 500;
      height: 48px;
      justify-content: center;
      letter-spacing: .25px;
      line-height: normal;
      max-width: 100%;
      overflow: visible;
      padding: 2px 24px;
      position: relative;
      text-align: center;
      text-transform: none;
      transition: box-shadow 280ms cubic-bezier(.4, 0, .2, 1),opacity 15ms linear 30ms,transform 270ms cubic-bezier(0, 0, .2, 1) 0ms;
      user-select: none;
      -webkit-user-select: none;
      touch-action: manipulation;
      width: auto;
      will-change: transform,opacity;
      z-index: 0;
    }

    .button-17:hover {
      background: #2992DC;
      color: white;
    }

    
    input[type=radio] {
  display: none;
  }

    .card {
  position: absolute;
  width: 60%;
  height: 100%;
  left: 0;
  right: 0;
  margin: auto;
  transition: transform .4s ease;
  cursor: pointer;
}

.container {
  width: 100%;
  max-width: 800px;
  max-height: 600px;
  height: 100%;
  transform-style: preserve-3d;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.cards {
  position: relative;
  width: 100%;
  height: 100%;
  margin-bottom: 20px;
}

img {
  width: 100%;
  height: 100%;
  border-radius: 10px;
  object-fit: cover;
}

#item-1:checked ~ .cards #song-3, #item-2:checked ~ .cards #song-1, #item-3:checked ~ .cards #song-2 {
  transform: translatex(-40%) scale(.8);
  opacity: .4;
  z-index: 0;
}

#item-1:checked ~ .cards #song-2, #item-2:checked ~ .cards #song-3, #item-3:checked ~ .cards #song-1 {
  transform: translatex(40%) scale(.8);
  opacity: .4;
  z-index: 0;
}

#item-1:checked ~ .cards #song-1, #item-2:checked ~ .cards #song-2, #item-3:checked ~ .cards #song-3 {
  transform: translatex(0) scale(1);
  opacity: 1;
  z-index: 1;
  
  img {
    box-shadow: 0px 0px 5px 0px rgba(81, 81, 81, 0.47);
  }
}

.player {
  background-color: #fff;
  border-radius: 8px;
  min-width: 320px;
  padding: 16px 10px;
}

.upper-part {
  position: relative;
  display: flex;
  align-items: center;
  margin-bottom: 12px;
  height: 36px;
  overflow: hidden;
}

.play-icon{ margin-right: 10px; }

.song-info {
  width: calc(100% - 32px);
  display: block;
}

.song-info .title {
  color: #403d40;
  font-size: 14px;
  line-height: 24px;
}

.sub-line {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.subtitle, .time {
  font-size: 12px;
  line-height: 16px;
  color: #c6c5c6;
}

.time {
  font-size: 12px;
  line-height: 16px;
  color: #a5a5a5;
  font-weight: 500;
  margin-left: auto;
}

.progress-bar {
  height: 3px;
  width: 100%;
  background-color: #e9efff;
  border-radius: 2px;
  overflow: hidden;
}

.progress {
  display: block;
  position: relative;
  width: 60%;
  height: 100%;
  background-color: #2992dc;
  border-radius: 6px;
}

.info-area {
  width: 100%;
  position: absolute;
  top: 0;
  left: 30px;
  transition: transform .4s ease-in;
}

#item-2:checked ~ .player #test {
  transform: translateY(0);
}

#item-2:checked ~ .player #test  {
  transform: translateY(-40px);
}

#item-3:checked ~ .player #test  {
  transform: translateY(-80px);
}

      
</style>
