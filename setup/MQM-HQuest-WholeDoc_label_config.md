<View>
  <Header value="Translation Error Annotation (MQM)" />
  
  <View style="display: flex; gap: 20px;">
    <!-- Left side: scrollable text area -->
    <View style="flex: 2; position: relative;">
      <Text name="text" value="$text" />
    </View>
    
    <!-- Right side: fixed controls with increased width -->
    <View style="flex: 1; position: sticky; top: 0; max-height: 100vh; overflow-y: auto;">
      <!-- Main Error Categories -->
      <Labels name="label" toName="text">
        <Label value="Terminology" background="#6CD97E" />
        <Label value="Accuracy" background="#FF4A4A" />
        <Label value="Linguistic Conventions" background="#5AA3E8" />
        <Label value="Style" background="#D89EFF" />
        <Label value="Locale Conventions" background="#FFAF4F" />
        <Label value="Audience Appropriateness" background="#FFC0CB" />
      </Labels>
          
      <!-- Error Subcategories -->
      <View whenRegionSelected="true">
        <Choices name="subcategories" toName="text" perRegion="true" layout="inline">
          <Header value="Subcategories" />
          <Choice value="TERM: Does not match glossary" hotkey="7" />
          <Choice value="TERM: Inconsistent use" hotkey="8" />
          <Choice value="TERM: Overly consistent use" hotkey="9" />
          <Choice value="TERM: Wrong term" hotkey="0" />
          <Choice value="ACC: Mistranslation" hotkey="q" />
          <Choice value="ACC: Addition" hotkey="w" />
          <Choice value="ACC: Omission" hotkey="e" />
          <Choice value="ACC: Shouldn't be translated" hotkey="t" />
          <Choice value="ACC: Wasn't translated" hotkey="a" />
          <Choice value="STYLE: Text-type conventions" hotkey="g" />
          <Choice value="STYLE: Organizational style" hotkey="z" />
          <Choice value="STYLE: Third-party style" hotkey="x" />
          <Choice value="STYLE: External reference" hotkey="c" />
          <Choice value="STYLE: Language register" hotkey="v" />
          <Choice value="STYLE: Unnatural style" hotkey="b" />
          <Choice value="STYLE: Inconsistent style" hotkey="y" />
          <Choice value="LING: Grammar" hotkey="s" />
          <Choice value="LING: Punctuation" hotkey="d" />
          <Choice value="LING: Spelling" hotkey="f" />
          <Choice value="LOC: Number" hotkey="i" />
          <Choice value="LOC: Currency" hotkey="o" />
          <Choice value="LOC: Measurement" hotkey="p" />
          <Choice value="LOC: Date" hotkey="j" />
          <Choice value="AUD: Cultural-specific reference" hotkey="k" />
          <Choice value="AUD: Offensive" hotkey="l" />
        </Choices>
      </View>
      
      <!-- Severity selection only appears after region selection - displayed horizontally -->
      <View whenRegionSelected="true">
        <Choices name="severity" toName="text" perRegion="true" layout="inline">
          <Header value="Severity" />
          <Choice value="Neutral" />
          <Choice value="Minor" />
          <Choice value="Major" />
          <Choice value="Critical" />
        </Choices>
      </View>
      
      <!-- Notes for each error only appears after region selection -->
      <View whenRegionSelected="true">
        <TextArea name="comments" toName="text"
                  placeholder="Explain the error referencing the source if needed." 
                  perRegion="true" 
                  rows="3" 
                  maxSubmissions="1" />
      </View>
    </View>
  </View>
  
  <!-- Document-level issues as a separate section -->
  <View style="margin-top: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 5px; background-color: #f9f9f9;">
    <Header value="Document-level Issues" />
    <TextArea name="document_issues" 
              toName="text" 
              placeholder="Note any issues that span multiple segments or apply to the entire document" 
              rows="4" 
              maxSubmissions="1" />
  </View>
  
  <!-- Overall metrics in separate sections with different background colors -->
  <View style="margin-top: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 5px; background-color: #f9f9f9;"> 
    <Header value="Overall Correspondence" /> 
    <Text name="correspondence_instruction" 
          value="Rate the overall quality of the translation in terms of its correspondence to the source content, where 1 star = major meaning differences, 4 stars = excellent correspondence." /> 
    <Rating name="overall_correspondence" toName="text" maxRating="4" icon="star" value="0" /> 
    <TextArea name="correspondence_comments" 
              toName="text" 
              placeholder="Additional overall comments about translation correspondence" 
              rows="3" 
              editable="true" 
              maxSubmissions="1" /> 
   </View>
  
   <View style="margin-top: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 5px; background-color: #f9f9f9;"> 
    <Header value="Overall Readability" /> 
    <Text name="readability_instruction" 
          value="Rate the overall quality of the translation in terms of its readability as a standalone document, where 1 star = difficult to read, 4 stars = reads naturally." /> 
    <Rating name="overall_readability" toName="text" maxRating="4" icon="star" value="0" /> 
    <TextArea name="readability_comments" 
              toName="text" 
              placeholder="Additional overall comments about translation readability" 
              rows="3" 
              editable="true" 
              maxSubmissions="1" /> 
   </View>
</View>
