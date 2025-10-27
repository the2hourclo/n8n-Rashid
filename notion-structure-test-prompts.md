# Notion Structure Validation Test Prompts

Run these prompts in **Claude Web App** (where you have Notion MCP connected) to validate your workspace structure is AI-readable.

---

## **Test 1: Database Discovery**

**Purpose:** Verify AI can find all your databases

**Prompt:**
```
List all databases you can find in my Notion workspace. For each database, show:
- Database name
- Number of entries
- Key properties (columns)
- Where it's located (which page)
```

**Expected Result:**
- Should find: Milestones, Key Targets, Projects, War Map, Habits & Routines, etc.
- Should show property names
- Should identify location (Rashid OS vs. other pages)

**Success Criteria:** ✅ AI finds all your core databases

---

## **Test 2: Page Structure Reading**

**Purpose:** Verify AI can read your hub pages

**Prompt:**
```
Please read my "Rashid OS 2.0" page and tell me:
1. What databases are on this page?
2. Are they source databases or linked views?
3. What other content is on this page?
4. Show me the overall structure
```

**Expected Result:**
- Lists all databases on Rashid OS
- Identifies them as source databases
- Shows page structure

**Success Criteria:** ✅ AI correctly maps Rashid OS structure

---

## **Test 3: Linked Views vs. Source**

**Purpose:** Verify AI understands linked views

**Prompt:**
```
Compare these two pages:
1. "Rashid OS 2.0"
2. "Alignment Board"

For each page, tell me:
- What databases appear on it?
- Are they source databases or linked views?
- Do they have any filters applied?
- What's the relationship between them?
```

**Expected Result:**
- Identifies Rashid OS as source
- Identifies Alignment Board as linked views
- Explains they point to same data

**Success Criteria:** ✅ AI distinguishes source from views

---

## **Test 4: Relation Traversal (Upward)**

**Purpose:** Verify AI can follow relations from child to parent

**Prompt:**
```
Find any one action item in my War Map database.

Then follow its relations UPWARD through the hierarchy:
1. What Project does it belong to?
2. What Key Target does that Project support?
3. What Milestone does that Target support?
4. What Vision does that Milestone support?

Show me the complete chain.
```

**Expected Result:**
```
Action Item: [Name]
  ↑ belongs to
Project: [Name]
  ↑ supports
Key Target: [Name]
  ↑ supports
Milestone: [Name]
  ↑ supports
Vision: [Name]
```

**Success Criteria:** ✅ AI successfully traverses entire hierarchy upward

---

## **Test 5: Relation Traversal (Downward)**

**Purpose:** Verify AI can follow relations from parent to children

**Prompt:**
```
Read my Vision (or active vision if it's a database).

Then follow the hierarchy DOWNWARD:
1. What Milestones support this Vision?
2. For the first Milestone, what Key Targets support it?
3. For the first Key Target, what Projects are working toward it?
4. For the first Project, what Action Items exist?

Show me the complete tree.
```

**Expected Result:**
```
Vision: [Name]
  ↓ supported by
├── Milestone 1: [Name]
│   ↓ supported by
│   ├── Key Target 1: [Name]
│   │   ↓ supported by
│   │   ├── Project 1: [Name]
│   │   │   ↓ has actions
│   │   │   ├── Action Item 1
│   │   │   └── Action Item 2
```

**Success Criteria:** ✅ AI successfully traverses entire hierarchy downward

---

## **Test 6: Context-Aware Generation**

**Purpose:** Verify AI can read context and generate based on it

**Prompt:**
```
I want to add a new Milestone to my Vision.

STEP 1: Read my current Vision
STEP 2: Read my existing Milestones
STEP 3: Based on the Vision and what Milestones I already have, suggest ONE new milestone that would fill a gap

Format your response:
- Vision Summary: [what you read]
- Existing Milestones: [list them]
- Suggested New Milestone: [your suggestion]
- Rationale: [why this fills a gap]
```

**Expected Result:**
- AI reads actual Vision content
- AI reads actual Milestones
- AI generates suggestion based on real data (not generic)

**Success Criteria:** ✅ Suggestion is specific to YOUR vision and gaps

---

## **Test 7: Database Property Reading**

**Purpose:** Verify AI can read specific properties accurately

**Prompt:**
```
Read my Projects database and show me:
1. How many projects exist?
2. How many have Status = "In Progress"?
3. List the properties that exist in this database
4. For one project, show me ALL its property values
```

**Expected Result:**
- Accurate count
- Accurate filtered count
- Complete list of properties (RICE scores, status, relations, etc.)
- Full property dump for one project

**Success Criteria:** ✅ AI accurately reads properties and values

---

## **Test 8: Filtered View Reading**

**Purpose:** Verify AI respects (or ignores) view filters

**Prompt:**
```
First, read my Projects database directly and tell me how many total projects exist.

Then, go to my Alignment Board page, look at the Projects view there, and tell me how many projects are shown.

Explain any difference.
```

**Expected Result:**
- First count: Total projects in database
- Second count: Filtered projects on Alignment Board
- Explanation of filter applied

**Success Criteria:** ✅ AI distinguishes full database from filtered view

---

## **Test 9: Multi-Database Query**

**Purpose:** Verify AI can query across multiple databases

**Prompt:**
```
Show me a strategic overview:
1. How many Milestones do I have?
2. How many Key Targets in total?
3. How many Projects are "In Progress"?
4. How many Action Items are "To Do"?
5. Calculate: What % of my total action items are complete?
```

**Expected Result:**
- Accurate counts from each database
- Correct percentage calculation
- AI demonstrates it can read multiple databases in one query

**Success Criteria:** ✅ AI queries multiple databases accurately

---

## **Test 10: Relationship Validation**

**Purpose:** Verify all relations are properly set up

**Prompt:**
```
Check the relationship structure of my strategic planning system:

1. Milestones database: What property links to Vision? What property shows Key Targets?
2. Key Targets database: What property links to Milestone? What property shows Projects?
3. Projects database: What property links to Key Target? What property shows Action Items?
4. War Map database: What property links to Projects?

Report any missing or broken relations.
```

**Expected Result:**
- Lists all relation property names
- Confirms bidirectional setup
- Identifies any missing relations

**Success Criteria:** ✅ All relations are properly configured

---

## **How to Use These Tests**

### **Run Them in Order:**
1. Start with Test 1 (Discovery)
2. If that works, move to Test 2-3 (Structure)
3. Then Test 4-5 (Relations)
4. Then Test 6-10 (Advanced)

### **Document Results:**
For each test, note:
- ✅ **PASS**: AI performed as expected
- ⚠️ **PARTIAL**: AI got some things right, some wrong
- ❌ **FAIL**: AI couldn't complete the test

### **Common Issues & Fixes:**

**Issue:** AI can't find a database
**Fix:** Make sure database isn't deeply nested; move to workspace level

**Issue:** AI can't follow relations
**Fix:** Check relation property names are clear and consistent

**Issue:** AI reads filtered view instead of full database
**Fix:** Be explicit in prompt: "Read the full Projects database, not any filtered views"

**Issue:** AI gets confused by naming
**Fix:** Use consistent, descriptive names (no abbreviations)

---

## **After Testing**

Once you've run all tests, you'll know:
- ✅ What AI can reliably do with your structure
- ⚠️ What needs clarification in prompts
- ❌ What structural changes you need to make

Then you can build your production prompts with confidence!

---

## **Next Steps After Validation**

1. **Document What Works:** Create a "Prompting Guide" in your Notion with successful prompt patterns
2. **Fix Issues:** Restructure any parts that AI struggled with
3. **Build Production Prompts:** Create the 50+ prompts for your Strategic Planning System
4. **Test Autonomous Agents:** Move to Claude Code for scheduled agent testing

---

**Remember:** Run these in Claude Web App where you have Notion MCP connected!