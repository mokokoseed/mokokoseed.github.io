---
layout: default
title: "Main/World Questline Guide"
description: "Use this guide to reference how far you've completed the various World questlines on Lost Ark."
---
<style>
.outer {
  height: 100vh;
  min-width: 20vw;
  flex: 1;
}



//-- 

.progress-steps {
  $gap: 20px;
  $line-height: 20px;
  $bullet-radius: 5px;
  $line-thick: 2px;
  $strip-color: #333;
  $next-color: #666;
  $current-color: #333;
  
  $prev-color: #333;
  

  display: inline-flex;
  height: 100%;
  padding: 5vh 10%;

  > div {
    display: flex;
    flex-direction: column;
    color: $prev-color;

    &.left {
      padding-right: $gap;
      text-align: right;
      
      // Line
      div {
        &:last-of-type:after {
          display: none;
        }
        
        &:after {
          content: "";
          background: fade_out($strip-color, .9); //rgba(0, 0, 0, 0.6);
          border-radius: 2px;
          position: absolute;
          right: -$gap;
          top: $line-height/2;
          height: 101%;
          width: 1px;
          transform: translateX(50%);
        }
      }
    }

    &.right {
      padding-left: $gap;

      div {        
        &.prev {          
            &:after {
              transition: none;
            }
        }
        
        &.current {
          color: $current-color;
          font-weight: bold;

          &:before {
            background: $current-color;
            padding: $bullet-radius * 2;
            transition: all 0.2s .15s cubic-bezier(0.175, 0.885, 0.32, 2);
          }

          &:after {
            height: 0%;
            transition: height .2s ease-out;
          }

          ~ div {
            color: $next-color;
            
            &:before {
              background: $next-color;
              padding: $bullet-radius * 0.5;
            }

            &:after {
              height: 0%;
              transition: none;
            }
          }
        }

        // Dot
        &:before {
          content: "";
          background: $strip-color;
          padding: $bullet-radius;
          border-radius: 50%;
          position: absolute;
          left: -$gap;
          top: $line-height/2;
          transform: translateX(-50%) translateY(-50%);
          transition: padding 0.2s ease;
        }

        // Line
        &:after {
          content: "";
          background: $strip-color; //rgba(0, 0, 0, 0.6);
          border-radius: 2px;
          position: absolute;
          left: -$gap;
          top: $line-height/2;
          height: 101%;
          width: $line-thick;
          transform: translateX(-50%);
          transition: height 0.2s ease;
        }
      }
    }

    div {
      flex: 1;
      //outline: 1px solid rgba(0, 0, 0, 0.1);
      position: relative;
      line-height: $line-height;
      cursor: default;
      min-height: 30px;
      
      &:last-of-type {
        flex: 0;
      }
    }
  }
}

.dark .progress-steps {  
  background: #333;
  
  $gap: 20px;
  $line-height: 20px;
  $bullet-radius: 5px;
  $line-thick: 2px;
  $strip-color: lightgray;
  $pending-color: #666;

  display: inline-flex;
  height: 100%;
  width: 100%;
  padding: 5vh 10%;

  > div {
    display: flex;
    flex-direction: column;
    color: #ccc;

    &.left {
      padding-right: $gap;
      text-align: right;
      
      // Line
      div {
        &:last-of-type:after {
          display: none;
        }
        
        &:after {
          content: "";
          background: fade_out($strip-color, .95); //rgba(0, 0, 0, 0.6);
          border-radius: 2px;
          position: absolute;
          right: -$gap;
          top: $line-height/2;
          height: 101%;
          width: 1px;
          transform: translateX(50%);
        }
      }
    }

    &.right {
      padding-left: $gap;

      div {        
        &.prev {          
            &:after {
              transition: none;
            }
        }
        
        &.current {
          color: white;
          font-weight: bold;

          &:before {
            background: white;
            padding: $bullet-radius * 2;
            transition: all 0.2s .15s cubic-bezier(0.175, 0.885, 0.32, 2);
          }

          &:after {
            height: 0%;
            transition: height .2s ease-out;
          }

          ~ div {
            color: $pending-color;
            
            &:before {
              background: $pending-color;
              padding: $bullet-radius * 0.5;
            }

            &:after {
              height: 0%;
              transition: none;
            }
          }
        }

        // Dot
        &:before {
          content: "";
          background: $strip-color;
          padding: $bullet-radius;
          border-radius: 50%;
          position: absolute;
          left: -$gap;
          top: $line-height/2;
          transform: translateX(-50%) translateY(-50%);
          transition: padding 0.2s ease;
        }

        // Line
        &:after {
          content: "";
          background: $strip-color; //rgba(0, 0, 0, 0.6);
          border-radius: 2px;
          position: absolute;
          left: -$gap;
          top: $line-height/2;
          height: 101%;
          width: $line-thick;
          transform: translateX(-50%);
          transition: height 0.2s ease;
        }
      }
    }

    div {
      flex: 1;
      //outline: 1px solid rgba(0, 0, 0, 0.1);
      position: relative;
      line-height: $line-height;
      cursor: default;
      min-height: 30px;
      
      &:last-of-type {
        flex: 0;
      }
    }
  }
}

.done.current {  
  color: #62af0b !important;
    
  &:before {
    background: #62af0b !important;
  }
}

.dark .done.current {  
  color: lightgreen !important;
    
  &:before {
    background: lightgreen !important;
  }
}
</style>

<h1>Main/World Questline Guide</h1>
<div class="d-flex align-items-start">
  <div class="nav flex-column nav-pills me-3" id="myPill" role="tablist" aria-orientation="vertical">
    {% for quest in site.data.questline %}
    <button class="nav-link" id="{{ quest.area }}-tab" data-toggle="pill" href="#{{ quest.area }}" type="button" role="tab">{{ quest.area }}</button>
    {% endfor %}
  </div>
  <div class="tab-content">
    {% for quest in site.data.questline %}
    <div class="tab-pane fade {% if quest.area == 'Tortoyk' %}show active{% endif %}" id="{{ quest.area }}" role="tabpanel">
    <div class="outer">
      <div class="progress-steps">
      <div class="right">
      {% for entry in quest.quests %}
          <div>{{ entry.quest }}</div>
      {% endfor %}
      </div>
    </div>  
    </div>  
      
    <ol>
    {% for entry in quest.quests %}
    <li>{{ entry.quest }}</li>
    {% endfor %}
    </ol>
    </div>
    {% endfor %}
  </div>
</div>

