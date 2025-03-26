<template>
    <header class="header">
        <div class="logo">
            <a href="/" class="logo">
                <img src="@/assets/icons/header-logo.svg" alt="kinetic-logo" height="30" />
            </a>
        </div>
        <div class="contact">
            <span><strong>Talk to a Consolidation Speacialist</strong></span>
            <img src="@/assets/icons/phone.svg" alt="phone-icon" width="14" height="14" /> 
            <span>(888) 888-8888</span>
        </div>
    </header>
</template>

<style scoped>
.header {
 background-color: #fff;
 border-bottom: 1px solid #ddd;
 display: flex;
 justify-content: space-between;
 padding: 1.25rem 12rem;
 position: sticky;
 top: 0;
 z-index: 1000;
}

.contact {
 align-items: center;
 color: #1d529e;
 display: flex;
 flex-wrap: wrap;
 gap: 0.5rem;
 margin-left: 1.25rem;
}

@media (max-width: 992px) {
  .header {
    align-items: center;
    flex-direction: column;
    gap: 0.625rem;
    padding: 1.25rem 2rem;
  }
}

</style>