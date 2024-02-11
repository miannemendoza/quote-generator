<template>

    <section class="quote">
        <div class="quote-content">
          
            {{quote.content}}
        </div>
        <div class="quote-author">
            -  {{quote.author}}
        </div>
    </section>
   
    
</template>

<script>
export default{
    props: ['quote'],
    methods: {
        getCopy(){
            document.addEventListener('DOMContentLoaded',function(){
  let copyButton = document.getElementsByTagName('button');
      copyButton.addEventListener('click', function () {
          navigator.clipboard
              .writeText(document.getElementById('copy-text').innerText)
              .then(
                  success => console.log("text copied"), err => console.log("error copying text")
              );
      });
});
        }
    }
}
</script>

<style lang="scss">

.quote{
    position: relative;
    background-color: white;
    padding: 10px;
   
    min-height: 200px;
    max-width: 720px;
    margin: 7px auto;
    background: white;
    border-radius: 20px;
    color: var(--dark);
   
    &-content{
       position: relative;
       padding: 48px 32px;
       border-radius: 16px;
        font-size: 30px;
        line-height: normal;
       &:before, &:after{
            content: "''";
        }

    }
    &-author{
        font-style: italic;
        padding-right: 10px;
        text-align: center;
        margin-top: -31px;
    }

    button{
    border: none;
    outline: none;
    background-color: var(--primary);
    border-radius: 10px;
    float: right;
    color: var(--light);
    font-size: 15px;
    font-weight: 700;
    transition: 0.4s;
    &:hover {
      background-color: var(--secondary);
    }
  }
}

</style>