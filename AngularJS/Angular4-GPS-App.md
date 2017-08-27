# Angular 4 GPS Activity Mapping App

<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/angular.png" width="180px" height="auto" />
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/heroku.png" width="200px" height="auto" />
</p>


# Steps to Build the project

## Installations

**1.** Create Angular App by Angular CLI

`ng new GPS-App`

`cd GPS-App`

`ng serve`

**2.** Generate Components

`ng generate component activity-list` generates `component.css/.html/.ts/.spec.ts` files and updates `app.module.ts`

`ng generate component map`

**3.** Update `activity-list.component.ts`

    import { IActivity } from '../shared/activity.model';
    ....
    export...
    ...
    activities: IActivity[];
    
**4.** Create `src/app/shared` folder and create 2 files in that `activities.ts` `activity.model.ts`

In `activity.model.ts`, add

    export interface IActivity {

      id: number
      name: string
      date: Date
      comments?: string //optional with ?
      distance?: number
      gpxData: string //gpx is XML format. Change to geoJSON

    }
    
In `activities.ts`, add activity data

    import { IActivity } from './activity.model';

      export const SAVED_ACTIVITIES: IActivity[] = [
        {
          "id" : 1,
          "name" : "Main Bike Trails",
          "date" : new Date('06/01/2017'),
          "distance" : 16.2,
          "comments" : "Nice day, cool temps",
          "gpxData": '../../assets/gpx/1.gpx'
        }
      ]


