---
layout: default
title: Services
---

<style>
    .services-container {
        margin-bottom: 18px;
        display: flex;
        gap: 18px;
    }
    .service-card {
        border-radius: 15px;
        box-shadow: 0px 0px 15px black;
        width: 0;
        flex-grow: 1; flex-shrink: 1; flex-basis: 0;
        border: 3px solid #20282e;
        padding: 20px;
    }
    .service-card > h2{
        text-align: center;
        padding-bottom: 5px;
    }
    .column-design {
        display: flex;
    }
    .service-card > div > img {
        display: block;
        margin-left: auto;
        margin-right: auto;
    }
    .email {
        font-size: 64px
    }
    /* Mobile */
    @media (max-width: 750px) {
        .services-container {
            flex-direction: column;
        }
        
        .service-card {
            width: auto;
            border: 3px solid #20282e;
            padding: 20px;
        }
        .email {
            font-size: 24px
        }
    }
</style>

<div style="text-align: center;">
    <h2 style="font-size:42px;">Services</h2>
    <p>Need help with your project?</p>
    <img src="/assets/images/services/panas.png" height="190px"/>
</div>

<div class="services-container">
    <div class="service-card">
        <h2><a href="#godot">Godot</a></h2>
        <div>
            <div>
                <p>Godot is a wonderful engine, we can help you with basically anything you need with your Godot project: fixing bugs, fixing optimization problems, implementing custom tools and systems, and more!</p>
            </div>
            <img src="/assets/images/services/godot.png" height="256px"/>
        </div>
    </div>
</div>
<div class="services-container">
    <div class="service-card">
        <h2><a href="#steam">Steam services</a></h2>
        <div>
            <div>
                <p>We can publish your game to Steam and integrate Steam services.</p>
                <p>Achievements, cloud saves, Steam Deck compatibility, and more!</p>
            </div>
            <img src="/assets/images/services/steam.png" height="256px"/>
        </div>
    </div>
    <div class="service-card">
        <h2><a href="#ci-and-automation">CI environment and automation</a></h2>
        <div>
            <div>
                <p>Do you want to automate your build or release process? Do you know the benefits of automated testing? Let us help you kickstart a Continuous Integration environment and find out!</p>
            </div>
            <img src="/assets/images/services/servers.png" height="256px"/>
        </div>
    </div>
    <div class="service-card">
        <h2><a href="#testing-and-qa">Testing and QA</a></h2>
        <div>
            <div>
                <p>If you have a project that needs testing, we can design a test plan for it or perform manual exploratory or performance testing. But contact us during development and we will advise you on the best practices to ensure quality is maintained during development.</p>
            </div>
            <img src="/assets/images/services/testing.png" height="256px"/>
        </div>
    </div>
</div>
<div class="services-container">
    <div class="service-card">
        <h2><a href="#vr-ar">VR and AR</a></h2>
        <div>
            <div>
                <p>We do VR and AR projects!</p>
            </div>
            <img src="/assets/images/services/vr.png" height="256px"/>
        </div>
    </div>
    <div class="service-card">
        <h2><a href="#porting">Porting</a></h2>
        <div>
            <div>
                <p>We can port your project to a different platform: PC, mobile, web, or console.</p>
            </div>
            <img src="/assets/images/services/platforms.png" height="256px"/>
        </div>
    </div>
</div>
<div class="services-container">
    <div class="service-card">
        <h2><a href="#unity">Unity</a></h2>
        <div>
            <div>
                <p>Unity is no stranger to us! from mobile games, VR and AR, web games, we've been using Unity for years...</p>
            </div>
            <img src="/assets/images/services/unity.png" height="256px"/>
        </div>
    </div>
    <div class="service-card">
        <h2><a href="#art">Video game art</a></h2>
        <div>
            <div>
                <p>You need help with the artistic part of the project? 2D Sprites? 3D models and animations? Shaders? UI and UX? You name it!</p>
            </div>
            <img src="/assets/images/services/art.png" height="256px"/>
        </div>
    </div>
</div>

## 💬 [Tell us about your project](#contact)

Do you have more questions, need help with your project, or want to know more?

<p class="email" ><a href="mailto: {{ site.data.social-media.email.href }}">{{ site.data.social-media.email.href }}</a></p>
