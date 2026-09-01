# FRSC Mobility Course - Road Safety & Responsible Mobility Platform

A comprehensive digital learning platform for FRSC (Federal Road Safety Corps) standardized road safety education in Nigeria.

## Overview

This is a mobile-first, interactive learning platform that guides students through:
- **Phase 1**: Digital Road Safety Education (15 modules)
- **Phase 2**: Simulation & Driving Readiness (Hardware simulator sessions)
- **Phase 3**: Accredited Driving School (On-road practical training)
- **Phase 4**: Official FRSC Driver's License (Certification & issuance)

## Features

### 📚 Interactive Learning
- 15 comprehensive modules covering road safety, traffic laws, defensive driving
- FRSC Standardization Programme (DSSP) aligned curriculum
- Learning outcomes clearly mapped to each module
- Visual topic tags and progress tracking

### 🎯 Interactive Assessments
- Module-specific quiz questions
- Immediate feedback on answers
- XP reward system for correct answers
- Progress tracking from home dashboard

### 🤖 AI Assistant Integration
- "Ask Cubbes" feature for module clarifications
- Context-aware responses based on FRSC guidelines
- Simulated but ready for real API integration

### 📍 Booking & Scheduling
- Hardware simulator session booking
- Accredited driving school selection
- Location-based center discovery
- FRSC partner verification

### 📊 Progress Tracking
- Visual progress bar for Phase 1 completion
- Timeline tracker showing all 4 phases
- Status indicators (Completed, In Progress, Locked, Unlocked)
- XP/Points system

## Project Structure

```
FRSC Mobility Course/
├── index.html          # Main application file (all-in-one)
├── README.md           # Project documentation
├── CLAUDE.md           # Development notes
└── assets/            # (Future) Images, icons, branding
```

## Getting Started

### Quick Start
1. Open `index.html` in a modern web browser
2. The app is fully self-contained with inline CSS and JavaScript
3. No build process or dependencies required

### Features Available
- **Home**: Dashboard with progress overview
- **Learn**: Browse all 15 modules
- **Module Content**: Read lessons, take quizzes, ask AI questions
- **Bookings**: Schedule simulator sessions and driving school lessons
- **Tracker**: View FRSC licensing pathway progress

## Technology Stack

- **HTML5**: Semantic markup
- **CSS3**: Custom properties (CSS variables), responsive design
- **Vanilla JavaScript**: All interactivity without dependencies
- **Mobile-First Design**: Optimized for 480px viewport (scales responsively)

## Data Structure

All modules are stored in the `modulesData` array within the script:
- 15 modules with complete curriculum content
- Learning outcomes, topics, and quiz questions
- Status tracking (completed, active, unlocked)
- FRSC alignment indicators

## Customization

### Styling
All colors and design tokens are defined as CSS variables in `:root`:
- `--primary`: Main brand color (#1E3A8A)
- `--accent`: Secondary accent (#0D9488)
- `--success`: Success state (#16A34A)
- etc.

### Content
Edit the `modulesData` array to:
- Add/modify modules
- Update quiz questions
- Change learning outcomes
- Adjust FRSC alignment labels

## Integration Points (Future)

- **Backend API**: Module progress persistence
- **User Authentication**: Login/registration system
- **Real AI Assistant**: Integration with Claude API or similar
- **Payment Processing**: Booking and certification fees
- **Email Notifications**: Booking confirmations, certificate issuance
- **Database**: Student progress, booking records, certifications

## FRSC Alignment

This platform aligns with the **FRSC Decentralised Standardization Support Programme (DSSP)**, ensuring all content meets official national road safety education standards for Nigeria.

## License

Internal project for Cubbes - FRSC Mobility Course Program

## Contact

For questions or feature requests, contact the development team.
